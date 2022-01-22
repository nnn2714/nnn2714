- 👋 Hi, I’m @nnn2714
- 👀 I’m interested in ...
- 🌱 I’m currently learning ...
- 💞️ I’m looking to collaborate on ...
- 📫 How to reach me ...

<!---
nnn2714/nnn2714 is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->--// Services \\--
local ReplicatedStorage = game:GetService("ReplicatedStorage")
local Players = game:GetService("Players")

--// Variables \\--
local Player = Players.LocalPlayer
local StatsChange = ReplicatedStorage:WaitForChild("Remotes"):WaitForChild("StatsChange")
local Storage = ReplicatedStorage:WaitForChild("CS_Keys"):WaitForChild("CS_Storage_Key")

--// Get Styles \\--
local Styles = {}
for _, A_1 in next, Storage:GetChildren() do
    table.insert(Styles, A_1.Value)
end
table.sort(Styles)

--// UI Library \\--
local Library = loadstring(game:HttpGetAsync('https://raw.githubusercontent.com/Just-Egg-Salad/roblox-scripts/main/uwuware'))()
local Window = Library:CreateWindow("Style Change by [CW]")
Window:AddList({
    text = "Style",
    values = Styles,
    callback = function(A_2)
        for _, A_1 in next, Storage:GetChildren() do
            if A_1.Value == A_2 then
                StatsChange:FireServer("CombatStyle", {
                    Base = {Position = Player.Character.HumanoidRootPart.Position},
                    CombatStyle = {Value = A_1.Name}
                })
            end
        end
    end
})
Library:Init()
