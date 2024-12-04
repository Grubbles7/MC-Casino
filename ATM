-- Constants for RedNet channels
local CHANNELS = {
    DEVELOPER = 1,
    SLOT_MACHINE = 2,
    ATM = 3,
    LEADERBOARD = 4
}

-- Constants for item values and transaction settings
local ITEM_VALUES = {
    gold_nugget = 1,
    iron_nugget = 2,
    emerald = 5,
    diamond = 10
}

local TRANSACTION_FEE = 0.05 -- 5% fee
local VIP_BONUS_RATE = 0.10 -- 10% bonus for VIPs

-- Storage for transaction history
local transactionHistory = {}

-- Function to fetch settings from the developer console
local function fetchSettings()
    rednet.open("back")
    rednet.broadcast("REQUEST_SETTINGS", CHANNELS.DEVELOPER)
    local senderId, message = rednet.receive(CHANNELS.DEVELOPER, 5)
    if message then
        ITEM_VALUES = message.item_values or ITEM_VALUES
        TRANSACTION_FEE = message.transaction_fee or TRANSACTION_FEE
        VIP_BONUS_RATE = message.vip_bonus_rate or VIP_BONUS_RATE
        print("Settings updated from Developer Console.")
    else
        print("Failed to fetch settings. Using defaults.")
    end
end

-- Function to validate the disk
local function validateDisk()
    local diskSide = peripheral.find("disk_drive")
    if not diskSide then
        return nil, "No disk detected. Please insert a disk."
    end

    local diskID = peripheral.call(diskSide, "getID")
    if not diskID then
        return nil, "Invalid disk. Please use a valid disk."
    end

    rednet.broadcast({type = "validate_disk", uid = diskID}, CHANNELS.DEVELOPER)
    local _, response = rednet.receive(CHANNELS.DEVELOPER, 5)
    if response and response.valid then
        return diskID, nil
    else
        return nil, "Unauthorized disk. Access denied."
    end
end

-- Function to deposit items
local function depositItems(diskID, items)
    local totalValue = 0
    for item, count in pairs(items) do
        local itemValue = ITEM_VALUES[item] or 0
        totalValue = totalValue + (itemValue * count)
    end

    local fee = totalValue * TRANSACTION_FEE
    local netValue = totalValue - fee

    -- Log transaction
    table.insert(transactionHistory, {type = "deposit", diskID = diskID, value = netValue, fee = fee})

    print("Deposited items worth: " .. netValue .. " (Fee: " .. fee .. ")")
end

-- Function to withdraw items
local function withdrawItems(diskID, amount, isVIP)
    local bonus = 0
    if isVIP then
        bonus = amount * VIP_BONUS_RATE
    end

    -- Log transaction
    table.insert(transactionHistory, {type = "withdrawal", diskID = diskID, value = amount, bonus = bonus})

    print("Withdrew items worth: " .. amount .. " (Bonus: " .. bonus .. ")")
end

-- Ensure the modem is opened
local function openModem()
    local sides = {"left", "right", "top", "bottom", "front", "back"}
    for _, side in ipairs(sides) do
        if peripheral.isPresent(side) and peripheral.getType(side) == "modem" then
            rednet.open(side)
            print("Modem opened on side: " .. side)
            return true
        end
    end
    print("No modem found. Please attach a modem to the computer.")
    return false
end

-- Main ATM function
local function atm()
    if not openModem() then
        return
    end
    fetchSettings()
    while true do
        print("=== ATM ===")
        print("1. Deposit Items")
        print("2. Withdraw Items")
        print("3. Exit")
        local choice = io.read()

        if choice == "1" then
            local diskID, err = validateDisk()
            if not diskID then
                print(err)
            else
                -- Example items to deposit
                local items = {gold_nugget = 10, diamond = 2}
                depositItems(diskID, items)
            end
        elseif choice == "2" then
            local diskID, err = validateDisk()
            if not diskID then
                print(err)
            else
                print("Enter amount to withdraw: ")
                local amount = tonumber(io.read())
                if amount then
                    local isVIP = false -- Placeholder for VIP check
                    withdrawItems(diskID, amount, isVIP)
                else
                    print("Invalid amount. Please enter a number.")
                end
            end
        elseif choice == "3" then
            break
        else
            print("Invalid choice. Please select a valid option.")
        end
    end
end

-- Startup script and termination protection
local function startup()
    while true do
        local ok, err = pcall(atm)
        if not ok then
            print("Error: " .. err)
        end
        sleep(1) -- Prevents tight loop in case of repeated errors
    end
end

startup()
