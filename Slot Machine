-- Constants for RedNet channels
local CHANNELS = {
    DEVELOPER = 1,
    SLOT_MACHINE = 2,
    ATM = 3,
    LEADERBOARD = 4
}

-- Constants
local REDNET_CHANNEL = 2
local PROGRESSIVE_JACKPOT_CONTRIBUTION = 0.1

-- Symbols and Weights
local symbols = {"Cherry", "Bell", "Bar", "Seven", "Jackpot"}
local symbol_weights = {40, 30, 20, 7, 3} -- Percent probabilities

-- Progressive Jackpot and VIP Multiplier
local progressive_jackpot = 0
local settings = {}
local vip_multiplier = 1

-- Fetch Settings from Dev Console
local function fetchSettings()
    rednet.open("back")
    rednet.broadcast("REQUEST_SETTINGS", CHANNELS.DEVELOPER)
    local senderId, message = rednet.receive(CHANNELS.DEVELOPER, 5)
    if message then
        settings = message.settings
        vip_multiplier = message.vip_multiplier or 1
        print("Settings updated from Developer Console.")
    else
        print("Failed to fetch settings. Using defaults.")
    end
end

-- Notify Unauthorized Disk
local function notifyUnauthorizedDisk(uid)
    rednet.broadcast({type = "unauthorized_disk", uid = uid}, CHANNELS.DEVELOPER)
    print("Unauthorized disk detected: " .. uid)
end

-- Disk Validation
local function validateDisk()
    local diskSide = peripheral.find("disk_drive") -- Find the disk drive peripheral
    if not diskSide then
        return nil, "No disk detected."
    end

    local diskID = peripheral.call(diskSide, "getID") -- Use peripheral.call to get the disk ID
    if not diskID then
        return nil, "Invalid disk."
    end

    rednet.broadcast({type = "validate_disk", uid = diskID}, CHANNELS.DEVELOPER)
    local _, response = rednet.receive(CHANNELS.DEVELOPER, 5)
    if response and response.valid then
        return diskID, nil
    else
        notifyUnauthorizedDisk(diskID)
        return nil, "Unauthorized disk."
    end
end

-- Spin Reels
local function spinReels()
    print("Spinning reels...")
    return {"Cherry", "Bell", "Bar"}
end

-- Calculate Winnings
local function calculateWinnings(bet, results, isVIP)
    print("Calculating winnings...")
    return 100
end

-- Function to display spinning animation
local function displaySpinningAnimation()
    print("Displaying spinning animation...")
end

-- Main Game Loop
local function playGame()
    fetchSettings()
    while true do
        print("=== Slot Machine ===")
        print("1. Insert Disk to Play")
        print("2. Exit")
        local choice = io.read()

        if choice == "1" then
            local diskID, err = validateDisk()
            if not diskID then
                print(err)
            else
                print("Enter your bet amount: ")
                local bet = tonumber(io.read())
                if bet then
                    displaySpinningAnimation()
                    local results = spinReels()
                    local isVIP = false -- Placeholder for VIP check
                    local winnings = calculateWinnings(bet, results, isVIP)
                    print("Results: " .. table.concat(results, " | "))
                    print("You won: " .. winnings .. " coins!")
                else
                    print("Invalid bet amount.")
                end
            end
        elseif choice == "2" then
            break
        else
            print("Invalid choice.")
        end
    end
end

-- Startup script and termination protection
local function startup()
    while true do
        local ok, err = pcall(playGame)
        if not ok then
            print("Error: " .. err)
        end
        sleep(1)
    end
end

startup()
