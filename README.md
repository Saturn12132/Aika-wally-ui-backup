# Aika-wally-ui-backup
--thanks trashs for the documentation
---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
--GUI customization
--Basically customize the color of certain things in ur gui such as the main color, secondary, etc etc...(Pretty self explanatory)
--This is a custom black and white gui color i quickly put up, idk wut it looks like but this is just an example
--NOTE: THIS PART IS NOT NEEDED, YOU CAN DELETE THIS IF YOU JUST WANT TO USE THE DEFAULT UI COLORS, THIS IS JUST AN EXAMPLE!!!

_G.MainColor = Color3.fromRGB(0,0,0) -- 0,0,0 are just RGB colors and u can usually get them from a hex wheel or wutever im pretty sure u already know that
_G.SecondaryColor = Color3.fromRGB(0,0,0)
_G.TertiaryColor = Color3.fromRGB(15, 15, 15)
_G.SliderColor = Color3.fromRGB(255,255,255)
_G.ButtonColor = Color3.fromRGB(255,255,255)
_G.ToggleColor = Color3.fromRGB(255,255,255)
_G.ArrowColor = Color3.fromRGB(255,255,255)
_G.MainTextColor = Color3.fromRGB(255,255,255)
_G.PointerColor = Color3.fromRGB(0,0,0)
_G.DraggerCircleColor = Color3.fromRGB(255,255,255)
_G.BindColor = Color3.fromRGB(255,255,255)
---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
--Creating Windows/Folders

local library = loadstring(game:HttpGet(('https://raw.githubusercontent.com/Saturn12132/Aika-wally-ui-backup/main/Uilib')))() --[[ !!DONT REMOVE THIS!! this is pretty important and its basically the brains for the entire thing ]]--

local w = library:CreateWindow("WINDOW NAME") -- Creates a window

local b = w:CreateFolder("FOLDER NAME") -- Creates the folder(U will put here your buttons,etc)

local c = w:CreateFolder("Credits")  -- obviously u can make more than 1 folder within a window (this is just an example)

--this pretty self explanatory and easy
--EXAMPLE: (if u want to make another window and put a credits folder in it)
local secondWin = library:CreateWindow("Second Window")
local credits = secondWin:CreateFolder("Credits")

--obviously u can put whatever you want in between the ""
credits:Label("Credits: trashs#1049 ",{
   TextSize = 17; -- Self Explaining
   TextColor = Color3.fromRGB(255,255,255); -- Self Explaining
   BgColor = Color3.fromRGB(30, 30, 30); -- Self Explaining
})
---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
--Functions inside a folder you created
--We are using "b" (local b = w:CreateFolder("FOLDER NAME")) as an example in here meaning if "b:Label" ,the Label function will be under the "b" folder
--Obviously you can make multiple of each function/ For example: you can make multiple different buttons that will execute different scripts in each one of them (DUHHHHHHH)
--If you want to change the name of the name or text, just edit out what's in between the ""

b:Label("WHATEVER YOU WANT TO PUT IN THE LABEL",{
   TextSize = 25; -- Self Explaining
   TextColor = Color3.fromRGB(255,255,255); -- Self Explanatory
   BgColor = Color3.fromRGB(69,69,69); -- Self Explanatory
})
   
b:Button("BUTTON NAME",function()
   print("hey")
   --or wutever script u want here
end)

b:Toggle("TOGGLE NAME",function(bool) --ama use "autoQuest as an example//you will need  to  create a "local autoQuest = false"
   autoQuest= bool -- basically it will toggle the "local autoQuest" into true/false
   -- you can plug in a simple script right here (EXAMPLE:)
   if autoQuest == true then
       print("AutoQuest = Enabled")
   else
       print("AutoQuest = Disabled")
   end
   --[[ !!IMPORTANT!!: if you want to use some type of loop (example: while wait() do//Etc.) I DO NOT RECOMMEND putting it within this function because it will bug and break the toggle button. SOLUTION: Separate it from the function or the script and just put it on the very bottom of the script (i will give an example in the end of this "Guide" using the same examples) ]]--
end)

b:Slider("SLIDER NAME",{
   min = 10; -- min value of the slider
   max = 50; -- max value of the slider
   precise = true; -- max 2 decimals
},function(value) --ofc u can change the "value" into something else like "number" or "afngkag" wutever u want rlly (duh)
   print(value)
   -- or wutever you want to do with the "value"
end)

b:Dropdown("DROPDOWN NAME",{"A","B","C"},true,function(mob) --replaces the current title "DROPDOWN NAME" with the option you pick from the table//"mob" can also be changed to wutever
   print(mob)
   -- or a script like this (this is an EXAMPLE)
     if mob == "A" then -- pretty ez and self explanatory
     -- script
     elseif mob == "B" then
     -- script
     elseif mob == "C" then
     --script
   end
end)

b:Bind("Bind",Enum.KeyCode.C,function() --Default bind/Im not familiar of this, but you wil be able to choose wutever key you want to bind it with in the gui and it will fire da script
   print("Yes")
   --wutever script u want ig
end)

b:Box("Box","number",function(value) -- "number" or "string"//im not familiar with this, ive never used this before lmao
   print(value)
end)

b:DestroyGui() --pretty self explanatory and useful, it will destroy the gui but it wont kill any functions already running (i think)
---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
--Scripts
--This is what I do when I make a gui, i usually separate the loop scripts from  the toggle.
--Note: I DONT THINK this applies the the "button" (loops should work with the button)
--Toggle Example: (with loops or wutever)
while wait(1) do
   if autoQuest == true then
       local args = {
           [1] = "GamesReborn"
       }
       game:GetService("ReplicatedStorage").Functions.Quest:InvokeServer(unpack(args))
       local args = {
           [1] = "GamesReborn"
       }
       game:GetService("ReplicatedStorage").Events.Quest:FireServer(unpack(args))
   end
end
---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
-- This part is not made by me, i just copied it from the other guide just incase someone needs this info
--[[
How to refresh a dropdown:
1)Create the dropdown and save it in a variable
local yourvariable = b:Dropdown("Hi",yourtable,function(a)
   print(a)
end)
2)Refresh it using the function
yourvariable:Refresh(yourtable)
How to refresh a label:
1)Create your label and save it in a variable
local yourvariable = b:Label("Pretty Useless NGL",{
   TextSize = 25; -- Self Explaining
   TextColor = Color3.fromRGB(255,255,255);
   BgColor = Color3.fromRGB(255, 255, 255)
})
2)Refresh it using the function
yourvariable:Refresh("Hello") It will only change the text ofc
]]--
