-- Wait for the "Frame" inside "StarterGui.Emotes"
local emotesFrame = game:GetService("StarterGui"):WaitForChild("Emotes"):WaitForChild("Frame")

-- Now that the "Frame" is found, you can interact with it
print(emotesFrame.Name .. " has been found!")

-- Example: changing the background color of the frame to red
emotesFrame.BackgroundColor3 = Color3.fromRGB(255, 0, 0)

-- Set the ZIndex of the frame to ensure it's interactable
emotesFrame.ZIndex = 10  -- Higher value, in front of other elements

-- Function to check if the frame is "clickable"
local function isFrameClickable()
    -- Check if the frame is behind anything else with a higher ZIndex
    local parent = emotesFrame.Parent
    local frontGui = parent:FindFirstChildOfClass("GuiObject") -- Find any GUI object in front
    if frontGui then
        if frontGui.ZIndex > emotesFrame.ZIndex then
            return false -- The frame is behind something
        end
    end
    return true
end

-- Example usage:
if isFrameClickable() then
    print("The frame is clickable!")
else
    print("The frame is behind something and not clickable.")
end

-- Wait for 0.1 seconds
wait(0.1)

-- Print "lala" after the wait
print("lala")>
