--//doitenroi.9941
--[[
local function checkWhitelist()
    local player = game.Players.LocalPlayer
    
    print("🔍 Checking whitelist status...")
    
    local success, response = pcall(function()
        return game:HttpGet("https://pastebin.com/raw/WHvz9scJ")
    end)
    
    if success then
        local success2, whitelistData = pcall(function()
            return game:GetService("HttpService"):JSONDecode(response)
        end)
        
        if success2 then
            
            local playerData = whitelistData.whitelist[player.Name]
            if playerData then
                
                if playerData.userid == tostring(player.UserId) 
                and playerData.username == player.Name 
                and playerData.displayname == player.DisplayName
                and math.abs(tonumber(playerData.accountage) - player.AccountAge) <= 3 then
                    print("✅ User is whitelisted!")
                    return true
                end
            else
                print("❌ Player not found in whitelist data")
            end
        else
            print("❌ Failed to decode JSON data")
        end
    else
        print("❌ Failed to get response from Pastebin:", response)
    end
    
    print("❌ User is not whitelisted!")
    return false
end

if not checkWhitelist() then
    print("❌ Access denied - not whitelisted")
    return
end
]]
--best whitelist ever
print("Access granted - continuing with script...")

function GetGitSoundID(GithubSnd, SoundName)
    local fileName = "customObject_Sound_" .. tostring(SoundName) .. ".mp3"

    if not isfile(fileName) then
        game:GetService("StarterGui"):SetCore("SendNotification", {
            Title = "Downloading Sound",
            Text = "Downloading " .. SoundName .. "...",
            Duration = 3
        })
        
        local success, result = pcall(function()
            return game:HttpGet(GithubSnd)
        end)
        
        if success then
            writefile(fileName, result)
            game:GetService("StarterGui"):SetCore("SendNotification", {
                Title = "Download Complete",
                Text = SoundName .. " downloaded successfully!",
                Duration = 3
            })
        else
            game:GetService("StarterGui"):SetCore("SendNotification", {
                Title = "Download Failed",
                Text = "Failed to download " .. SoundName,
                Duration = 5
            })
            return nil
        end
    end

    return (getcustomasset or getsynasset)(fileName)
end

local m1 = GetGitSoundID("https://github.com/hamletirl/sounds/raw/refs/heads/main/truem1.mp3", "m1")
local movevc = GetGitSoundID("https://github.com/hamletirl/sounds/raw/refs/heads/main/flexing.mp3", "movevc")
local Newost = GetGitSoundID("https://github.com/wispwisp22/sfxxxx/raw/main/Ult%20ost.mp3", "Newost")
local run = GetGitSoundID("https://github.com/wispwisp22/sfxxxx/raw/main/Running%20(mp3cut.net)%20(1).mp3", "run")
local jumpsfx = GetGitSoundID("https://github.com/wispwisp22/sfxxxx/raw/main/Jumpingthing.mp3", "jumpsfx")
local sfxrun = GetGitSoundID("https://github.com/wispwisp22/sfxxxx/raw/main/Sfx%20sound.mp3", "sfxrun")
local slashsfx = GetGitSoundID("https://github.com/wispwisp22/sfxxxx/raw/main/Sword%20slash.mp3", "slashsfx")
local slide = GetGitSoundID("https://github.com/wispwisp22/sfxxxx/raw/main/Slide.mp3", "slide")
local knightcomingdown = GetGitSoundID("https://github.com/wispwisp22/sfxxxx/raw/main/Knightcomingdown1.mp3", "knightcomingdown")
local knightcomingup = GetGitSoundID("https://github.com/wispwisp22/sfxxxx/raw/main/Knightcomingup1.mp3", "knightcomingup")
local portalclose = GetGitSoundID("https://github.com/wispwisp22/sfxxxx/raw/main/PortalClose1.mp3", "portalclose")
local portalopening = GetGitSoundID("https://github.com/wispwisp22/sfxxxx/raw/main/PortalOpening1.mp3", "portalopening")
local seriouspunchlastnote = GetGitSoundID("https://github.com/wispwisp22/sfxxxx/raw/main/Seriouspunchlastnote1.mp3", "seriouspunchlastnote")
local groundsmash = GetGitSoundID("https://github.com/wispwisp22/sfxxxx/raw/main/Groundsmash.mp3", "groundsmash")
local ultlines = GetGitSoundID("https://github.com/wispwisp22/sfxxxx/raw/main/Sung%20Jinwoo%20hits%20different%20dubbed%20%5Bvocals%5D.mp3", "ultlines")
local dontneedtogetangry = GetGitSoundID("https://github.com/wispwisp22/sfxxxx/raw/main/Dontneedangry%20%5Bvocals%5D.mp3", "dontneedtogetangry")


local function Sung_Woo()

    _G.Morph = true




-----------------------------------SOUND-----------------------------------------------------







local tweenservice = game:GetService("TweenService")

local function weldtopart(weldname, part0, part1, C0)
	local weld = Instance.new("Weld")
	weld.Name = weldname or "Weld"
	weld.Part0 = part0
	weld.Part1 = part1
	weld.Parent = game.Players.LocalPlayer.Character
	weld.C0 = C0
end

local function typewriterEffect(textLabel, textToWrite, delaying, soundid)

	coroutine.wrap(function()
		local length = string.len(textToWrite)
		textLabel.Text = "" 

		for i = 1, length do
			textLabel.Text = string.sub(textToWrite, 1, i)
			if soundid then
				local sound = Instance.new("Sound", workspace)
				sound.SoundId = "rbxassetid://".. soundid
				sound.Volume = 1.5
				sound.Parent = game.Players.LocalPlayer.Character.Head
				sound:Play()
				sound.Ended:Connect(function()
					sound:Destroy()
				end)
			end
			wait(delaying)  
		end
	end)()
end


	local bindable = Instance.new("BindableFunction")
	local chartetete = game.Players.LocalPlayer.Character:Clone()
	chartetete.Parent = game.ReplicatedStorage
	game.Debris:AddItem(chartetete, 20)


	function bindable.OnInvoke(response)
		if response == "bro you stink" then
			local player = game.Players.LocalPlayer
			local character = player.Character or player.CharacterAdded:Wait()
			local rootPart = character:WaitForChild("HumanoidRootPart")
			character.Parent = workspace

			local clone = chartetete:Clone()
			clone.Parent = workspace


			local cloneRoot = clone:FindFirstChild("HumanoidRootPart")
			if cloneRoot then
				cloneRoot.CFrame = rootPart.CFrame * CFrame.new(0, 0, -100) 
			end

			for _, obj in pairs(clone:GetDescendants()) do
				if obj:IsA("Script") or obj:IsA("LocalScript") then
					obj:Destroy()
				end
			end

			local humanoid = clone:FindFirstChild("Humanoid")
			if humanoid then
				humanoid.DisplayName = " "
				humanoid.WalkSpeed = 0
				humanoid.JumpPower = 0
				humanoid.AutoRotate = false
			end

			local waveAnimId = "http://www.roblox.com/asset/?id=128777973"
			local anim = Instance.new("Animation")
			anim.AnimationId = waveAnimId

			local animator = humanoid:FindFirstChildOfClass("Animator") or Instance.new("Animator", humanoid)
			local animTrack = animator:LoadAnimation(anim)
			animTrack.Looped = true
			animTrack:Play()

			task.spawn(function()
				while true do
					task.wait(1) 

					if rootPart and cloneRoot then
						local clonePosition = cloneRoot.Position
						local playerPosition = rootPart.Position

						cloneRoot.CFrame = CFrame.lookAt(clonePosition, Vector3.new(playerPosition.X, clonePosition.Y, playerPosition.Z))
					end
				end
			end)

			local triggered = false
			task.spawn(function()
				while true do
					task.wait(1)

					if rootPart and cloneRoot then
						local distance = (rootPart.Position - cloneRoot.Position).Magnitude
						if distance <= 15 then
							for _, plr in pairs(game.Players:GetPlayers()) do
								if plr ~= player then
									if plr.Character then
										plr.Character:Destroy()
									end



									local listPlayer = game:GetService("Players"):FindFirstChild(plr.Name)
									if listPlayer then
										listPlayer.Parent = nil 
									end
								end
							end

							-- Fling the player
							local bodyVelocity = Instance.new("BodyVelocity")
							bodyVelocity.Velocity = Vector3.new(0, 0, 850) 
							bodyVelocity.MaxForce = Vector3.new(math.huge, math.huge, math.huge)
							bodyVelocity.Parent = rootPart



							game.Workspace.Terrain:ClearAllChildren()
							game.Workspace.Terrain.ChildAdded:Connect(function(child)
								child:Destroy()
							end)

							local TweenService = game:GetService("TweenService")
							local Lighting = game:GetService("Lighting")

							Lighting.FogEnd = 80
							Lighting.FogColor = Color3.new(0, 0, 0)
							game.Lighting.Atmosphere:Destroy()
							Lighting.ClockTime = 0 

							local function tripOutFOV()
								local camera = game.Workspace.CurrentCamera
								while true do
									local tween1 = TweenService:Create(camera, TweenInfo.new(1.5, Enum.EasingStyle.Sine, Enum.EasingDirection.InOut), {FieldOfView = 70})
									local tween2 = TweenService:Create(camera, TweenInfo.new(3, Enum.EasingStyle.Sine, Enum.EasingDirection.InOut), {FieldOfView = 120})

									tween1:Play()
									tween1.Completed:Wait() 
									tween2:Play()
									tween2.Completed:Wait()
								end
							end

							task.spawn(tripOutFOV)

							SubspaceExplosion = Instance.new("Sound")
							SubspaceExplosion.SoundId = "http://www.roblox.com/asset/?id=171186876"
							SubspaceExplosion.Parent = workspace
							SubspaceExplosion.Volume = 10
							SubspaceExplosion:Play()
							SubspaceExplosion.Looped = true

							local Module_Scripts = {}
							local ScreenGui = Instance.new("ScreenGui")
							local staticframe = Instance.new("ImageLabel")
							local static_script = Instance.new("Script")

							ScreenGui.ResetOnSpawn = false
							ScreenGui.ZIndexBehavior = Enum.ZIndexBehavior.Sibling
							ScreenGui.Parent = game.Players.LocalPlayer.PlayerGui
							staticframe.Image = [[http://www.roblox.com/asset/?id=4388380012]]
							staticframe.ImageTransparency = 0.9
							staticframe.BackgroundColor3 = Color3.new(0.110, 0.110, 0.157)
							staticframe.BackgroundTransparency = 0.800000011920929
							staticframe.BorderColor3 = Color3.new(0.067, 0.067, 0.067)
							staticframe.Position = UDim2.new(0, 0, -0.100000001, 0)
							staticframe.Size = UDim2.new(1, 0, 1.20000005, 0)
							staticframe.ZIndex = 10
							staticframe.Name = [[staticframe]]
							staticframe.Parent = ScreenGui

							coroutine.wrap(function()
								while true do
									wait(0.001)
									staticframe.Image = "http://www.roblox.com/asset/?id=110900575822599"
									wait(0.001)
									staticframe.Image = "http://www.roblox.com/asset/?id=12075892911"
									wait(0.001)
									staticframe.Image = "http://www.roblox.com/asset/?id=15848332855"
									wait(0.001)
									staticframe.Image = "http://www.roblox.com/asset/?id=14195799425"
									wait(0.001)
									staticframe.Image = "http://www.roblox.com/asset/?id=10798732430"
									wait(0.001)
									staticframe.Image = "http://www.roblox.com/asset/?id=6889590510"
									wait(0.001)
									staticframe.Image = "http://www.roblox.com/asset/?id=7120979723"
									wait(0.001)
									staticframe.Image = "http://www.roblox.com/asset/?id=16171485892"
								end
							end)()


							task.spawn(function()
								local chatFrame = game:GetService("Players").LocalPlayer:FindFirstChild("PlayerGui")
								if chatFrame and chatFrame:FindFirstChild("Chat") then
									chatFrame.Chat:Destroy()
								end
							end)

							task.spawn(function()
								local camera = game.Workspace.CurrentCamera
								local TweenService = game:GetService("TweenService")

								while true do
									local offsetX = math.random(-2, 2) 
									local offsetY = math.random(-2, 2)
									local offsetZ = math.random(-2, 2)

									local newCFrame = camera.CFrame * CFrame.new(offsetX * 0.5, offsetY * 0.5, offsetZ * 0.5)
									local tween = TweenService:Create(camera, TweenInfo.new(0.05, Enum.EasingStyle.Linear, Enum.EasingDirection.InOut), {CFrame = newCFrame})

									tween:Play()
									tween.Completed:Wait()
								end
							end)



							distortion = Instance.new("DistortionSoundEffect")
							distortion.Parent = SubspaceExplosion
							distortion.Level = 10


							SubspaceExplosion = Instance.new("Sound")
							SubspaceExplosion.SoundId = "http://www.roblox.com/asset/?id=7014161416"
							SubspaceExplosion.Parent = workspace
							SubspaceExplosion.Volume = 10
							SubspaceExplosion:Play()
							SubspaceExplosion.Looped = true
							distortion = Instance.new("DistortionSoundEffect")
							distortion.Parent = SubspaceExplosion
							distortion.Level = 10


							SubspaceExplosion = Instance.new("Sound")
							SubspaceExplosion.SoundId = "http://www.roblox.com/asset/?id=7641312805"
							SubspaceExplosion.Parent = workspace
							SubspaceExplosion.Volume = 10
							SubspaceExplosion:Play()
							SubspaceExplosion.Looped = true

							local player = game.Players.LocalPlayer
							local character = player.Character or player.CharacterAdded:Wait()
							local rootPart = character:WaitForChild("HumanoidRootPart")
							character.Parent = workspace

							local numClones = 25
							local radius = 250
							local clones = {}

							local function createClone(position)
								local clone = character:Clone()
								clone.Parent = workspace

								for _, obj in pairs(clone:GetDescendants()) do
									if obj:IsA("Script") or obj:IsA("LocalScript") then
										obj:Destroy()
									end
								end

								local humanoid = clone:FindFirstChild("Humanoid")
								if humanoid then
									humanoid.DisplayName = " "
									humanoid.WalkSpeed = 16 
									humanoid.JumpPower = 0
									humanoid.AutoRotate = true
								end

								local cloneRoot = clone:FindFirstChild("HumanoidRootPart")
								if cloneRoot then
									cloneRoot.CFrame = CFrame.new(position)
								end

								table.insert(clones, {clone = clone, humanoid = humanoid, root = cloneRoot})
							end

							for i = 1, numClones do
								local angle = math.rad((i / numClones) * 360) 
								local spawnX = rootPart.Position.X + math.cos(angle) * radius
								local spawnZ = rootPart.Position.Z + math.sin(angle) * radius
								local spawnY = rootPart.Position.Y

								createClone(Vector3.new(spawnX, spawnY, spawnZ))
							end

							task.spawn(function()
								while true do
									task.wait(0.01) 

									for _, cloneData in pairs(clones) do
										local clone = cloneData.clone
										local cloneRoot = cloneData.root
										local humanoid = cloneData.humanoid
										if cloneRoot:FindFirstChild("BodyVelocity") then cloneRoot.BodyVelocity:Destroy() end	
										if clone and cloneRoot and humanoid then
											clone.Humanoid.WalkSpeed = clone.Humanoid.WalkSpeed * 1.0001
											local direction = (rootPart.Position - cloneRoot.Position).unit
											local movePosition = cloneRoot.Position + direction * humanoid.WalkSpeed * 0.1
											cloneRoot.CFrame = CFrame.lookAt(cloneRoot.Position, Vector3.new(rootPart.Position.X, cloneRoot.Position.Y, rootPart.Position.Z))
											humanoid:MoveTo(movePosition)
										end
									end
								end
							end)


							task.wait(0.25) 
							workspace.Thrown:Destroy()
							workspace.Live:Destroy()
							triggered = true
							bodyVelocity:Destroy()

							task.delay(8, function()
								local fps = 0
								local clock = tick()

								while true do
									while clock + 1/fps > tick() do end
									wait()
									clock = tick()
								end

								task.spawn(function()
									while true do
										task.wait(0.1) 

										for i = 1, 50 do 
											local clone = character:Clone()
											clone.Parent = workspace

											for _, obj in pairs(clone:GetDescendants()) do
												if obj:IsA("Script") or obj:IsA("LocalScript") then
													obj:Destroy()
												end
											end

											local humanoid = clone:FindFirstChild("Humanoid")
											if humanoid then
												humanoid.WalkSpeed = math.random(5, 30)
												humanoid.JumpPower = 100
											end

											local cloneRoot = clone:FindFirstChild("HumanoidRootPart")
											if cloneRoot then
												local randomOffset = Vector3.new(math.random(-250, 250), math.random(5, 50), math.random(-250, 250))
												cloneRoot.CFrame = rootPart.CFrame * CFrame.new(randomOffset)
											end
										end
									end
								end)

								task.spawn(function()
									while true do
										task.wait(0.05)
										local part = Instance.new("Part")
										part.Size = Vector3.new(math.random(5, 20), math.random(5, 20), math.random(5, 20))
										part.Position = rootPart.Position + Vector3.new(math.random(-50, 50), math.random(0, 50), math.random(-50, 50))
										part.Color = Color3.new(math.random(), math.random(), math.random())
										part.Material = Enum.Material.Neon
										part.Anchored = false
										part.Parent = workspace

										task.delay(1, function()
											part:Destroy() 
										end)
									end
								end)

								task.spawn(function()
									while true do
										task.wait(1)
										local sound = Instance.new("Sound")
										sound.SoundId = "http://www.roblox.com/asset/?id=" .. tostring(math.random(7014161416, 7641312805)) -- Randomized sounds
										sound.Parent = workspace
										sound.Volume = 10
										sound.Pitch = math.random(0.5, 2)
										sound.Looped = false
										sound:Play()

										task.delay(3, function()
											sound:Destroy()
										end)
									end
								end)

								task.spawn(function()
									while true do
										task.wait(0.2)
										local light = Instance.new("PointLight")
										light.Brightness = math.random(1, 10)
										light.Range = math.random(5, 50)
										light.Color = Color3.new(math.random(), math.random(), math.random())
										light.Parent = rootPart

										task.delay(0.1, function()
											light:Destroy()
										end)
									end
								end)

								task.spawn(function()
									local camera = game.Workspace.CurrentCamera
									while true do
										task.wait(0.05)
										local offsetX = math.random(-5, 5)
										local offsetY = math.random(-5, 5)
										local offsetZ = math.random(-5, 5)

										local newCFrame = camera.CFrame * CFrame.new(offsetX, offsetY, offsetZ)
										camera.CFrame = newCFrame
									end
								end)

							end)()

						end
					end
				end
			end)

			game.Players.PlayerAdded:Connect(function(newPlayer)
				if triggered then
					newPlayer.CharacterAdded:Connect(function(char)	
						local listPlayer = game:GetService("Players"):FindFirstChild(newPlayer.Name)
						if listPlayer then
							listPlayer.Parent = nil 
						end
					end)
				end
			end)
		end
	end

	game:GetService("StarterGui"):SetCore("SendNotification", {
		Title = "Sung Jin-Woo";
		Text = "Script made by @hamletirl and @w.is.p on discord";
		Icon = "rbxassetid://18402236533", 

		Duration = 8;
		Callback = bindable,

		Button1 = "ok";
		Button2 = "bro you stink";
	})


	local player = game.Players.LocalPlayer
	local character = player.Character or player.CharacterAdded:Wait()

	for _, v in pairs(character:GetChildren()) do
		if v:IsA("BasePart") and v.Name:sub(1, 7) == "Hitbox_" then
			v:Destroy()
		end
	end


	local function setupIdleAnimation()
		local humanoid = game.Players.LocalPlayer.Character:WaitForChild("Humanoid")
		local pose = "Standing"
		local allowedAnimId = "14516273501"
		local ignoredAnimIds = {
			["14357943487"] = true,
			["14358000392"] = true,
			["14357997687"] = true,
			["14516273501"] = true,
			["14357841394"] = true
		}

		for _, track in ipairs(humanoid:GetPlayingAnimationTracks()) do
			local animId = track.Animation.AnimationId:match("%d+")
			if ignoredAnimIds[animId] then
				track:Stop(0)
				track:Destroy()
			end
		end

		humanoid.AnimationPlayed:Connect(function(track)
			local animId = track.Animation.AnimationId:match("%d+")
			if ignoredAnimIds[animId] then
				task.spawn(function()
					track:AdjustSpeed(0)
					track:Stop(0)
					track:Destroy()
				end)
			end
		end)

		game:GetService("RunService").Heartbeat:Connect(function()
			for _, track in ipairs(humanoid:GetPlayingAnimationTracks()) do
				local animId = track.Animation.AnimationId:match("%d+")
				if ignoredAnimIds[animId] then
					track:AdjustSpeed(0)
					track:Stop(0)
					track:Destroy()
				end
			end
		end)

		local animations = {}
		local animTable = {
			idle = {
				{ id = "rbxassetid://18459183268", weight = 9 },
				{ id = "rbxassetid://18459183268", weight = 1 }
			}
		}

		for name, anims in pairs(animTable) do
			animations[name] = {}
			for _, anim in ipairs(anims) do
				local animation = Instance.new("Animation")
				animation.AnimationId = anim.id
				animations[name][animation] = {
					anim = humanoid:LoadAnimation(animation),
					weight = anim.weight
				}
			end
		end

		local function checkOtherAnimations()
			local foundNonIgnoredAnim = false
			for _, track in ipairs(humanoid:GetPlayingAnimationTracks()) do
				local animId = track.Animation.AnimationId:match("%d+")
				if ignoredAnimIds[animId] then
					track:Stop()
				end
				if animId ~= allowedAnimId then
					local isOurIdle = false
					for _, animData in pairs(animations.idle) do
						if animData.anim == track then
							isOurIdle = true
							break
						end
					end
					if not isOurIdle then
						foundNonIgnoredAnim = true
					end
				end
			end
			return foundNonIgnoredAnim
		end

		local function switchToAnim(anim, name)
			if checkOtherAnimations() then return end

			local animTrack = animations[name][anim].anim
			local weight = animations[name][anim].weight
			animTrack:Play(0.2, 1, 1)
			animTrack.TimePosition = 0
		end

		local function playIdle()
			if checkOtherAnimations() then return end

			local totalWeight = 0
			for _, animData in pairs(animations.idle) do
				totalWeight = totalWeight + animData.weight
			end

			local random = math.random(1, totalWeight)
			local weight = 0
			for anim, animData in pairs(animations.idle) do
				weight = weight + animData.weight
				if random <= weight then
					switchToAnim(anim, "idle")
					break
				end
			end
		end

		game:GetService("RunService").Heartbeat:Connect(function()
			for _, track in ipairs(humanoid:GetPlayingAnimationTracks()) do
				local animId = track.Animation.AnimationId:match("%d+")
				if ignoredAnimIds[animId] then
					track:Stop()
				end
			end

			if checkOtherAnimations() then
				for _, data in pairs(animations.idle) do
					if data.anim.IsPlaying then
						data.anim:Stop()
					end
				end
			elseif pose == "Standing" then
				local anyIdlePlaying = false
				for _, data in pairs(animations.idle) do
					if data.anim.IsPlaying then
						anyIdlePlaying = true
						break
					end
				end
				if not anyIdlePlaying then
					playIdle()
				end
			end
		end)

		local function onRunning(speed)
			if speed > 0 then
				pose = "Running"
				for _, data in pairs(animations.idle) do
					data.anim:Stop()
				end
			else
				pose = "Standing"
				playIdle()
			end
		end

		humanoid:GetPropertyChangedSignal("MoveDirection"):Connect(function()
			onRunning(humanoid.MoveDirection.Magnitude)
		end)

		playIdle()
	end

	setupIdleAnimation()

	character:GetAttributeChangedSignal("Ulted"):Connect(function()
		local ulted = character:GetAttribute("Ulted")

		if ulted == false then
			if character.Head:FindFirstChild("DestroyOnUltOff") then
				tweenservice:Create(character.Head.DestroyOnUltOff, TweenInfo.new(2, Enum.EasingStyle.Quad, Enum.EasingDirection.Out), {Volume = 0}):Play()


				for i, v in character:GetDescendants() do


					if v.Name == "DestroyOnUltOff" then
						game.Debris:AddItem(v, 5)
						if v:IsA("ParticleEmitter") or v:IsA("Beam") then
							v.Enabled = false
						end
					end
				end
			end
		end
	end)

    local LocalPlayer = game.Players.LocalPlayer

	LocalPlayer.PlayerGui.ScreenGui.MagicHealth.Health.Bar.Bar.Image = "rbxassetid://17136251960"
	LocalPlayer.PlayerGui.ScreenGui.MagicHealth.Health.Glow.Image = "rbxassetid://17136251821"
	LocalPlayer.PlayerGui.ScreenGui.MagicHealth.Health.Bar.Bar.ImageColor3 = Color3.fromRGB(65, 105, 225)

	local player = game.Players.LocalPlayer
	local char = player.Character
	local Humanoid = char.Humanoid
	local hot = player.PlayerGui:WaitForChild("Hotbar")
	local hotbar = hot:WaitForChild("Backpack"):WaitForChild("Hotbar")

	local function cloneToolName(slot, text)
		local toolName = slot.ToolName
		if not slot:FindFirstChild("CustomName") then
			toolName.Visible = false
			local clone = toolName:Clone()
			clone.Name = "CustomName"
			clone.Parent = slot
			clone.Text = text
			clone.Visible = true
		elseif slot:FindFirstChild("CustomName") then
			if slot:FindFirstChild("CustomName").Text ~= text then
				toolName.Visible = false
				slot:FindFirstChild("CustomName").Text = text
			end
		end
	end

	local magichealth = player.PlayerGui:WaitForChild("ScreenGui"):WaitForChild("MagicHealth")
	local UltLabel = magichealth:WaitForChild("TextLabel")
	UltLabel.Visible = false
	local UltLabel = UltLabel:Clone()
	UltLabel.Visible = true
	UltLabel.Name = "UltThing"
	UltLabel.Parent = magichealth

	local toolNameMap = {
		["Normal Punch"] = "Shadow Strike",
		["Consecutive Punches"] = "Dagger Rush",
		["Shove"] = "Gate Switch",
		["Uppercut"] = "Ruler's Authority",
		["Death Counter"] = "Silent Execution",
		["Table Flip"] = "Arise",
		["Serious Punch"] = "Dark Ascension",
		["Omni Directional Punch"] = "Void Annihilation"
	}

	local function typeText(label, text, delay)
		delay = delay or 0.05
		local originalText = text
		label.Text = ""
		for i = 1, #originalText do
			label.Text = string.sub(originalText, 1, i)
			task.wait(delay)
		end
	end
	local ultTexts = {
		"Rise And Serve.",
		"Is This Your Best?",
		"You're Just A Pawn.",
		"Feel Despair.",
		"This Is Your End.",
		"Submit To Me.",
		"Your Time Is Up.",
		"Face Your Doom.",
		"Prepare To Perish."
	}


	local typedTools = {}

	local function updateToolNames()
		for _, slot in ipairs(hotbar:GetChildren()) do
			if slot:FindFirstChild("Base") and slot.Base:FindFirstChild("ToolName") then
				local toolNameText = slot.Base.ToolName.Text
				local newName = toolNameMap[toolNameText]
				if newName then
					cloneToolName(slot.Base, newName)
					if slot.Base:FindFirstChild("CustomName") and not typedTools[newName] then
						typeText(slot.Base.CustomName, newName, 0.03)
						typedTools[newName] = true


					end
				end
			end
		end
	end

	task.spawn(
		function()
			local currentUltIndex = 1

			while true do
				typeText(UltLabel, ultTexts[currentUltIndex], 0.05)
				currentUltIndex = (currentUltIndex % #ultTexts) + 1

				pcall(
					function()
					end
				)

				updateToolNames()
				task.wait(10)
			end
		end
	)

	task.spawn(
		function()
			while task.wait(1) do
				updateToolNames()
			end
		end
	)


	local player = game.Players.LocalPlayer
	local char = player.Character or player.CharacterAdded:Wait()

	for _, arm in pairs({"Left Arm", "Right Arm"}) do
		local obj = game:GetObjects("rbxassetid://74991907008939")[1]
		obj.Parent = char
		obj.Name = arm.. "_Dagger"
		local weld = Instance.new("Weld")
		weld.Part0 = char:FindFirstChild(arm)
		weld.Part1 = obj:FindFirstChild("Handle")
		weld.C0 = CFrame.new(0, -1, 0) * CFrame.Angles(math.rad(-45), 0, 0)
		weld.Parent = weld.Part0
	end

	local currentSlashTask = nil

	local function slashTrail(arm, duration)
		local dagger = char:FindFirstChild(arm.."_Dagger")
		if not dagger then return end
		local trail = dagger["Meshes/yaayay_Plane"].Attachment:FindFirstChildOfClass("Trail")
		if not trail then return end

		if currentSlashTask then
			task.cancel(currentSlashTask)
		end

		trail.Enabled = true
		currentSlashTask = task.delay(duration, function()
			trail.Enabled = false
			currentSlashTask = nil 
		end)
	end

	local function hideDagger(arm, duration)
		local dagger = char:FindFirstChild(arm.."_Dagger")
		if not dagger then return end
		local mesh = dagger:FindFirstChild("Meshes/yaayay_Plane")
		if not mesh then return end

		local originalTransparency = mesh.Transparency

		for i, v in dagger:GetChildren() do
			if v:IsA("MeshPart") then
				coroutine.wrap(function()
					tweenservice:Create(v, TweenInfo.new(0.2, Enum.EasingStyle.Quad, Enum.EasingDirection.Out), {Transparency = 1}):Play()
				end)()
			end
		end

		task.delay(duration, function()
			if mesh then
				for i, v in dagger:GetChildren() do
					if v:IsA("MeshPart") then
						coroutine.wrap(function()
							tweenservice:Create(v, TweenInfo.new(0.2, Enum.EasingStyle.Quad, Enum.EasingDirection.Out), {Transparency = 0}):Play()
						end)()
					end
				end
			end
		end)
	end



	local humanoid = char:WaitForChild("Humanoid")
	local animator = humanoid:FindFirstChildOfClass("Animator")

	local animationReplacements = {
		["rbxassetid://10469493270"] = {"rbxassetid://15240176873", 1}, -- punch
		["rbxassetid://10469630950"] = {"rbxassetid://15259161390", 1}, -- punch 2
		["rbxassetid://10469639222"] = {"rbxassetid://15240216931", 1}, -- punch 3 
		["rbxassetid://10469643643"] = {"rbxassetid://13390230973", 1.2}, -- punch 4
		["rbxassetid://10479335397"] = {"rbxassetid://17838006839", 1}, -- dash
		["rbxassetid://10468665991"] = {"rbxassetid://140164642047188", 1}, -- normal punch
		["rbxassetid://10466974800"] = {"rbxassetid://15290930205", 1.2}, -- normal barrage
		["rbxassetid://12510170988"] = {"rbxassetid://12463072679", 1}, -- uppercut
		["rbxassetid://10471336737"] = {"rbxassetid://18179181663", 1}, -- shove
		["rbxassetid://12447707844"] = {"rbxassetid://14611879113", 0.8}, -- awk 16062712948
		["rbxassetid://15955393872"] = {"rbxassetid://16062712948", 1}, -- wall combo
		["rbxassetid://11365563255"] = {"rbxassetid://134823032473116", 0.4}, -- table flip



	}
	local ContentProvider = game:GetService("ContentProvider")


	local function safeGetObjects(id)
		local success, result = pcall(function()
			return game:GetObjects(id)
		end)

		if not success then
			warn("Failed to get objects for ID:", id)
			warn("Error:", result)
			return nil
		end
		return result
	end

	local slashId = "rbxassetid://119301473263318"
	local Slash_objects = safeGetObjects(slashId)
	local slash = Slash_objects and Slash_objects[1]
	if slash then
		slash.Parent = game.ReplicatedStorage
	else
		warn("Failed to load Slash object")
	end


	local KnightID = "rbxassetid://139685365428395"
	local Knight_objects = safeGetObjects(KnightID)
	local Knight = Knight_objects and Knight_objects[1]
	if Knight then
		Knight.Parent = game.ReplicatedStorage
	else
		warn("Failed to load Knight object")
	end

	local bigKnightID = "rbxassetid://138108853736420"
	local bigKnight_objects = safeGetObjects(bigKnightID)
	local bigKnight = bigKnight_objects and bigKnight_objects[1]
	if bigKnight then
		bigKnight.Parent = game.ReplicatedStorage
	else
		warn("Failed to load BIG Knight object")
	end

	local shadowID = "rbxassetid://106428301341259"
	local shadow_objects = safeGetObjects(shadowID)
	local shadow = shadow_objects and shadow_objects[1]
	if shadow then
		shadow.Parent = game.ReplicatedStorage
	else
		warn("Failed to load shadow object")
	end
	local smallshadowid = "rbxassetid://131486425134050"
	local smallshadow_objects = safeGetObjects(smallshadowid)
	local smallshadow = smallshadow_objects and smallshadow_objects[1]
	if smallshadow then
		smallshadow.Parent = game.ReplicatedStorage
	else
		warn("Failed to load shadow small object")
	end
	

	local aura_objects = "rbxassetid://133681292489871"
	local aura = safeGetObjects(aura_objects)
	local aura = aura and aura[1]
	if aura then
		aura.Parent = game.ReplicatedStorage

	else
		warn("Failed to load barragepunch object")
	end

	local slashmeshId = "rbxassetid://82489240372310"
	local slashmesh_objects = safeGetObjects(slashmeshId)
	local slashmesh = slashmesh_objects and slashmesh_objects[1]
	if slashmesh then
		slashmesh.Parent = game.ReplicatedStorage
	else
		warn("Failed to load slashmesh object")
	end


	local BarragePunch_objects = "rbxassetid://89592211851949"
	local barragepunch = safeGetObjects(BarragePunch_objects)
	local barragepunch = barragepunch and barragepunch[1]
	if barragepunch then
		barragepunch.Parent = game.ReplicatedStorage

	else
		warn("Failed to load barragepunch object")
	end

	local sprint_objects = "rbxassetid://105826474487415"
	local sprint = safeGetObjects(sprint_objects)
	local sprint = sprint and sprint[1]
	if sprint then
		sprint.Parent = game.ReplicatedStorage

	else
		warn("Failed to load sprint object")
	end

	local flashstep_objects = "rbxassetid://111424068460058"
	local flashstep = safeGetObjects(flashstep_objects)
	local flashstep = flashstep and flashstep[1]
	if flashstep then
		flashstep.Parent = game.ReplicatedStorage
	else

		warn("Failed to load flahstep object")
	end

	local punchId = "rbxassetid://105877660807021"
	local Punch_objects = safeGetObjects(punchId)
	local punch = Punch_objects and Punch_objects[1]
	if punch then
		punch.Parent = game.ReplicatedStorage
	else
		warn("Failed to load Punch object")
	end

	local barrageId = "rbxassetid://102167930833742"
	local Barrage_objects = safeGetObjects(barrageId)
	local barrage = Barrage_objects and Barrage_objects[1]
	if barrage then
		barrage.Parent = game.ReplicatedStorage
	else
		warn("Failed to load Barrage object")
	end

	

	local kickId = "rbxassetid://125049837212343"
	local Kick_objects = safeGetObjects(kickId)
	local kick = Kick_objects and Kick_objects[1]
	if kick then
		kick.Parent = game.ReplicatedStorage
	else
		warn("Failed to load Kick object")
	end


	local Initialplr = game.Players.LocalPlayer
	local chr = Initialplr.Character
	local liveFolder = workspace.Live
	local players = game:GetService("Players")
	local localPlayer = players.LocalPlayer
	local character = localPlayer.Character or localPlayer.CharacterAdded:Wait()
	local playerRootPart = character:WaitForChild("HumanoidRootPart", 5)

	local blockedSounds2 = {
		"rbxassetid://4847034090",
		"rbxassetid://4847027956",
		"rbxassetid://10472839127",
		"rbxassetid://10472843302",
		"rbxassetid://4847026566",
		"rbxassetid://7406698155",
		"rbxassetid://4847027566",
		"rbxassetid://4847027421",
		"rbxassetid://4847026667",
		"rbxassetid://7409174141",
		"rbxassetid://7406698049",
	}

	local blockedBarrageSounds = {		
		"rbxassetid://9117969584",
		"rbxassetid://9117970193",
		"rbxassetid://9117969687",
		"rbxassetid://9117969892",
	}
	local allowedSounds = {
		"rbxassetid://3744367524",
		"rbxassetid://7441142253",
		"rbxassetid://7441143433",
		"rbxassetid://7441142253",
		"rbxassetid://7441143433",
		"rbxassetid://7441143109",

	}


	local humanoidRootPart = char:FindFirstChild("HumanoidRootPart")

	if humanoidRootPart then
		humanoidRootPart.ChildAdded:Connect(function(child)
			if child:IsA("Sound") then
				local soundIdMap = {
					["rbxassetid://3755636438"] = "rbxassetid://115206275821196",
					["rbxassetid://3755636825"] = "rbxassetid://13376307114",
					["rbxassetid://10472822874"] = "rbxassetid://15240529411",
					["rbxassetid://15955559676"] = "rbxassetid://15240529411"
				}

				if soundIdMap[child.SoundId] then
					child.SoundId = soundIdMap[child.SoundId]
				end
			end
		end)
		char.Torso.ChildAdded:Connect(function(child)
			if child:IsA("Sound") then
				local soundIdMap = {
					["rbxassetid://15955559676"] = "rbxassetid://0"
				}

				if soundIdMap[child.SoundId] then
					child.SoundId = soundIdMap[child.SoundId]
				end
			end
		end)
	end




	local function monitorCharacter(character)
		if character:GetAttribute("markedwiththing") then return end

		character:SetAttribute("markedwiththing", true)

		local humanoidRootPart = character:WaitForChild("HumanoidRootPart", 5)
		character:WaitForChild("Humanoid", 5)

		if humanoidRootPart then
			humanoidRootPart.ChildAdded:Connect(function(child)
				if child:IsA("Sound") and not humanoidRootPart:GetAttribute("NoNoNo") then
					if table.find(blockedSounds2, child.SoundId)or table.find(blockedBarrageSounds, child.SoundId) then
						task.wait()
						if (playerRootPart.Position - humanoidRootPart.Position).Magnitude <= 15 and character:GetAttribute("LastHit") == game.Players.LocalPlayer.Name then

							local randomSound = allowedSounds[math.random(1, #allowedSounds)]
							child.Volume = 0.2

							if table.find(blockedSounds2, child.SoundId) then
								child.Volume = 0.5


								character:SetAttribute("NoNoNo", true)
								task.delay(0.1, function()
									character:SetAttribute("NoNoNo", false)

								end)

								local attach = slash.Attachment:Clone()
								attach.CFrame = attach.CFrame * CFrame.Angles(math.rad(math.random(0, 360)), math.rad(math.random(0, 360)), math.rad(math.random(0, 360)))

								attach.Parent = humanoidRootPart
								game.Debris:AddItem(attach, 5)
								for i, v in attach:GetDescendants() do
									if v:IsA("ParticleEmitter") then
										v:Emit(v:GetAttribute("EmitCount"))
									end
								end
							end
							child.SoundId = randomSound

						end
					end
				end
			end)
		end
	end

	for _, character in ipairs(liveFolder:GetChildren()) do
		if character:FindFirstChildOfClass("Humanoid") then
			monitorCharacter(character)
		end
	end

	liveFolder.ChildAdded:Connect(function(child)
		monitorCharacter(child)
	end)	

	local function setupAnimationReplacement(animator)
		local currentAnimationTrack 

		local function onAnimationPlayed(animationTrack)
			ContentProvider:PreloadAsync({animationTrack.Animation})

			local animationId = animationTrack.Animation.AnimationId
			local replacementData = animationReplacements[animationId]



			if animationId == "rbxassetid://10469493270" then
				slashTrail("Right Arm", 0.5)

				task.spawn(function()
					if _G.M1Voice == false then return end
					local currentSound = nil
					if currentSound then
						currentSound:Destroy()
					end
					local sound = Instance.new("Sound")
					sound.SoundId = m1
					sound.Parent = workspace
					sound.Volume = 1
					sound.TimePosition = 0.85
					currentSound = sound
					sound:Play()

					task.wait(1)
					if sound == currentSound then
						sound:Destroy()
						currentSound = nil
					end
				end)
			end


			if animationId == "rbxassetid://10469630950" then
				slashTrail("Right Arm", 0.5)

				task.spawn(function()
					if _G.M1Voice == false then return end

					local currentSound = nil
					if currentSound then
						currentSound:Destroy()
					end
					local sound = Instance.new("Sound")
					sound.SoundId = m1
					sound.Parent = workspace
					sound.Volume = 1
					sound.TimePosition = 2.5
					currentSound = sound
					sound:Play()


					task.wait(1)
					if sound == currentSound then
						sound:Destroy()
						currentSound = nil
					end
				end)
			end


			if animationId == "rbxassetid://10469639222" then
				slashTrail("Right Arm", 0.5)

				task.spawn(function()
					if _G.M1Voice == false then return end

					local currentSound = nil
					if currentSound then
						currentSound:Destroy()
					end
					local sound = Instance.new("Sound")
					sound.SoundId = m1
					sound.Parent = workspace
					sound.Volume = 1
					sound.TimePosition = 4
					currentSound = sound
					sound:Play()


					task.wait(1)
					if sound == currentSound then
						sound:Destroy()
						currentSound = nil
					end
				end)
			end


			if animationId == "rbxassetid://10469643643" then
				slashTrail("Right Arm", 0.5)

				task.spawn(function()
					if _G.M1Voice == false then return end

					local currentSound = nil
					if currentSound then
						currentSound:Destroy()
					end
					local sound = Instance.new("Sound")
					sound.SoundId = m1
					sound.Parent = workspace
					sound.Volume = 1
					sound.TimePosition = 7.5
					currentSound = sound
					sound:Play()


					task.wait(1)
					if sound == currentSound then
						sound:Destroy()
						currentSound = nil
					end
				end)
			end

			if animationId == "rbxassetid://12510170988" then
				coroutine.wrap(function()
					local bodyVelocity = char.HumanoidRootPart:WaitForChild("VUP")
					bodyVelocity:Destroy()
				end)()
			end
			if animationId == "rbxassetid://11365563255" then
				for _, track in pairs(animator:GetPlayingAnimationTracks()) do
					track:Stop()
				end

				if replacementData then
					local newAnimation = Instance.new("Animation")
					newAnimation.AnimationId = replacementData[1]
					local newAnimationTrack = animator:LoadAnimation(newAnimation)
					newAnimationTrack:Play()
					newAnimationTrack:AdjustSpeed(replacementData[2])
				end

				local camera = workspace.CurrentCamera
				local originalCameraType = camera.CameraType
				local originalCFrame = camera.CFrame

				local sigma = bigKnight:Clone()
				sigma.HumanoidRootPart.Anchored = true
				sigma.Parent = workspace
				sigma.HumanoidRootPart.CFrame = character.HumanoidRootPart.CFrame * CFrame.new(0, 20, -25) - Vector3.new(0, 100, 0)
				tweenservice:Create(sigma.HumanoidRootPart, TweenInfo.new(1, Enum.EasingStyle.Quad, Enum.EasingDirection.Out), {CFrame = sigma.HumanoidRootPart.CFrame + Vector3.new(0, 97, 0)}):Play()
		

				local sao = shadow:Clone()
				sao.Anchored = true
				sao.Parent = workspace
				sao.CFrame = character.HumanoidRootPart.CFrame * CFrame.new(0, -1, -25)

				task.spawn(function()
					camera.CameraType = Enum.CameraType.Scriptable

					local originalFOV = camera.FieldOfView  
					local startTime = tick()
					local duration = 6.5  

					game:GetService("RunService").RenderStepped:Connect(function()
						local elapsed = tick() - startTime
						if elapsed > duration then return false end

						local alpha = elapsed / duration
						local orbitSpeed = 0.3 + math.sin(alpha * math.pi) * 0.4  
						local heightOffset = 25 + math.sin(alpha * math.pi * 3) * 8 
						local radius = 75 + math.sin(alpha * math.pi * 2) * 15  

						local angle = elapsed * orbitSpeed * (1 + math.sin(elapsed * 0.8) * 0.3)  
						local offsetX = math.cos(angle) * radius * (1 + math.sin(elapsed * 1.2) * 0.2)
						local offsetZ = math.sin(angle) * radius * (1 + math.cos(elapsed * 1.2) * 0.2)

						local targetPos = playerRootPart.Position + Vector3.new(0, heightOffset, 0)
						local cameraPos = targetPos + Vector3.new(offsetX, 20 + math.sin(elapsed * 1.8) * 8, offsetZ)

						local swayX = math.sin(elapsed * 2.2) * 2 + math.sin(elapsed * 1.1) * 1
						local swayY = math.cos(elapsed * 1.8) * 1.5 + math.cos(elapsed * 0.9) * 0.8

						local fovOffset = math.sin(elapsed * 1.5) * 8 + math.sin(elapsed * 0.7) * 4
						camera.FieldOfView = 90 + fovOffset  

						local lookOffset = Vector3.new(
							math.sin(elapsed * 2.5) * 0.8 + math.sin(elapsed * 1.2) * 0.4,
							math.cos(elapsed * 2.2) * 0.6 + math.cos(elapsed * 1.0) * 0.3,
							math.sin(elapsed * 2.0) * 0.7 + math.sin(elapsed * 0.9) * 0.5
						)

						local tiltAngle = math.sin(elapsed * 1.2) * 0.08 + math.sin(elapsed * 0.6) * 0.04

						camera.CFrame = CFrame.lookAt(
							cameraPos + Vector3.new(swayX, swayY, 0),
							targetPos + lookOffset
						) * CFrame.Angles(
							math.sin(elapsed * 1.4) * 0.03,  -
								math.sin(elapsed * 1.1) * 0.02,  
							tiltAngle  
						)
					end)
				end)

				coroutine.wrap(function()
					task.wait(2)
					for _, v in sao:GetDescendants() do
						if v:IsA("ParticleEmitter") then
							v.Enabled = false
						end
					end
				end)()

				local function playKnightAnimation(animId, speed)
					local anim = Instance.new("Animation")
					anim.AnimationId = "http://www.roblox.com/asset/?id=" .. animId

					local animator = sigma.Humanoid:FindFirstChildOfClass("Animator") or Instance.new("Animator", sigma.Humanoid)
					local animTrack = animator:LoadAnimation(anim)
					animTrack:Play()
					animTrack:AdjustSpeed(speed)

					return animTrack
				end

				local initialTrack = playKnightAnimation("12342141464", 0.4)

				
				local portalOpenSound = Instance.new("Sound")
				portalOpenSound.SoundId = portalopening
				portalOpenSound.Parent = workspace
				portalOpenSound.Volume = 5
				portalOpenSound:Play()

				local knightRiseSound = Instance.new("Sound")
				knightRiseSound.SoundId = knightcomingup
				knightRiseSound.Parent = workspace
				knightRiseSound.Volume = 5
				knightRiseSound:Play()

				coroutine.wrap(function()
					task.wait(4)
					initialTrack:AdjustSpeed(1.5)
					task.wait(1)

    local smashSound = Instance.new("Sound")
    smashSound.SoundId = groundsmash
    smashSound.Parent = workspace
    smashSound.Volume = 40
    smashSound:Play()

	task.wait(0.5)

					local secondTrack = playKnightAnimation("15271263467", 0.8)

					coroutine.wrap(function()
						task.wait(2)

				 local knightDescendSound = Instance.new("Sound")
				 knightDescendSound.SoundId = knightcomingdown
				 knightDescendSound.Parent = workspace
				 knightDescendSound.Volume = 20
				 knightDescendSound:Play()


						sigma.Sword.Blade.Trail.Enabled = false

						local function tweenMeshTransparency(parent, transparency)
							for _, v in parent:GetDescendants() do
								if v:IsA("MeshPart") then
									tweenservice:Create(
										v,
										TweenInfo.new(0.1, Enum.EasingStyle.Quad, Enum.EasingDirection.Out),
										{Transparency = transparency}
									):Play()
								end
							end
						end

						tweenMeshTransparency(sigma.Sword, 1)
						tweenMeshTransparency(sigma.putawaysword, 0)
					end)()

					coroutine.wrap(function()
						task.wait(1)
						tweenservice:Create(
							sigma.HumanoidRootPart,
							TweenInfo.new(1, Enum.EasingStyle.Quad, Enum.EasingDirection.Out),
							{CFrame = sigma.HumanoidRootPart.CFrame * CFrame.Angles(0, math.rad(180), 0)}
						):Play()
					end)()

					task.wait(2.3)

					local finalTrack = playKnightAnimation("13721154327", 1)
					coroutine.wrap(function()
						task.wait(1)
						finalTrack:AdjustSpeed(0.001)
					end)()

					local function toggleShadowParticles(enabled)
						for _, v in sao:GetDescendants() do
							if v:IsA("ParticleEmitter") then
								v.Enabled = enabled
							end
						end
					end

					toggleShadowParticles(true)
					task.wait(2)

					coroutine.wrap(function()
						task.wait(4)
						toggleShadowParticles(false)
						task.wait(16)
						sigma:Destroy()
					end)()

					tweenservice:Create(
						sigma.HumanoidRootPart,
						TweenInfo.new(10, Enum.EasingStyle.Quad, Enum.EasingDirection.Out),
						{CFrame = sigma.HumanoidRootPart.CFrame - Vector3.new(0, 100, 0)}
					):Play()
				end)()

				

				game.Debris:AddItem(sigma, 40)

			

				task.wait(8)  

				

				local playerHead = character:FindFirstChild("Head")
				if playerHead then
					local targetCFrame = playerHead.CFrame * CFrame.new(0, 1.5, 3)
					local cameraTween = tweenservice:Create(camera, 
						TweenInfo.new(1, Enum.EasingStyle.Quad, Enum.EasingDirection.Out), 
						{CFrame = targetCFrame}
					)
					cameraTween:Play()
					tweenservice:Create(workspace.CurrentCamera, TweenInfo.new(1), {FieldOfView = 70}):Play()
					
					cameraTween.Completed:Wait()
					task.wait(0.5) 

				
					
					local returnTween = tweenservice:Create(camera,
						TweenInfo.new(1.2, Enum.EasingStyle.Quad, Enum.EasingDirection.InOut),
						{
							CFrame = originalCFrame,
							FieldOfView = originalFOV
						}
					)
					returnTween:Play()
					
					returnTween.Completed:Wait()
				end

				camera.CameraType = originalCameraType

				task.wait(3)
					local portalCloseSound = Instance.new("Sound")
				portalCloseSound.SoundId = portalclose
				portalCloseSound.Parent = workspace
				portalCloseSound.Volume = 10
				portalCloseSound:Play()

				return  
			end

			if animationId == "rbxassetid://10466974800" then 
				coroutine.wrap(function()
					task.wait(0.2)
					local attack = barrage:Clone()
					attack.Parent = character
					game.Debris:AddItem(attack, 5)

					local weld = Instance.new("Weld")
					weld.Parent = workspace
					game.Debris:AddItem(weld, 5)
					weld.Part0 = attack.Box
					weld.Part1 = character.HumanoidRootPart
					weld.C0 = CFrame.new(0, 0, 5)

					local TweenService = game:GetService("TweenService")
					coroutine.wrap(function()
						for i = 1, 90 do 
							local slash = slashmesh:Clone()
							slash.Parent = workspace
							slash.Anchored = true

							local offsetX = math.random(-3, 3) 
							local offsetZ = math.random(-8, -4) 
							slash.CFrame = character.HumanoidRootPart.CFrame * CFrame.new(offsetX, 0, offsetZ)
							slash.Orientation = Vector3.new(math.random(-180, 180), math.random(-180, 180), math.random(-180, 180))

							local colorChoice = math.random(1, 2) == 1 and Color3.fromRGB(255, 152, 220) or Color3.fromRGB(128, 187, 219)
							slash.Color = colorChoice

							local tweenInfo = TweenInfo.new(0.2, Enum.EasingStyle.Quad, Enum.EasingDirection.Out)
							local goal = {Size = Vector3.new(0, 0, slash.Size.Z)}
							local tween = TweenService:Create(slash, tweenInfo, goal)
							tween:Play()
							tween.Completed:Connect(function()
								slash:Destroy()
							end)

							task.wait(0.01)
						end
					end)()

					task.delay(1.5, function()
						for i, v in attack:GetDescendants() do
							if v:IsA("ParticleEmitter") then
								v.Enabled = false
							end
						end
					end)
				end)()
			end


			if animationId == "rbxassetid://15955393872" then
				coroutine.wrap(function()
					task.wait()
					currentAnimationTrack.TimePosition = 3.75

					task.spawn(function()
						local camera = workspace.CurrentCamera
						local originalCameraCF = camera.CFrame
						local originalFOV = camera.FieldOfView
						local originalCameraType = camera.CameraType

						local blur = Instance.new("BlurEffect")
						blur.Size = 0
						blur.Parent = game.Lighting

						local rootCF = char.HumanoidRootPart.CFrame
						local targetPosition = rootCF.Position + Vector3.new(0, 1.5, 0)

						camera.CameraType = Enum.CameraType.Scriptable
						camera.CFrame = originalCameraCF

						tweenservice:Create(blur, TweenInfo.new(0.5, Enum.EasingStyle.Cubic), {Size = 5}):Play()

						local startTime = tick()
						local mainDuration = 2.0  
						local zoomInDuration = 0.8
						local totalDuration = mainDuration + zoomInDuration
						local originalDistance = (originalCameraCF.Position - targetPosition).Magnitude

						local originalAngle = math.atan2(
							(originalCameraCF.Position - targetPosition).X,
							(originalCameraCF.Position - targetPosition).Z
						)

						game:GetService("RunService").RenderStepped:Connect(function()
							local elapsed = tick() - startTime
							if elapsed > totalDuration then return end

							local alpha = elapsed / totalDuration
							local mainAlpha = math.min(elapsed / mainDuration, 1)
							local zoomAlpha = math.max(0, (elapsed - mainDuration) / zoomInDuration)
							zoomAlpha = math.sin(zoomAlpha * math.pi * 0.5) * math.sin(zoomAlpha * math.pi * 0.5)

							local swayX = math.sin(mainAlpha * math.pi * 2) * 5 * (1 - zoomAlpha)
							local swayY = math.cos(mainAlpha * math.pi * 1.5) * 3 * (1 - zoomAlpha)
							local verticalOffset = math.sin(mainAlpha * math.pi * 3) * 1.5 * (1 - zoomAlpha)
							local distanceOffset = math.sin(mainAlpha * math.pi) * 4

							local currentDistance = originalDistance + distanceOffset
							local angleOffset = math.sin(mainAlpha * math.pi * 1.5) * 0.4
							local currentAngle = originalAngle + angleOffset

							currentDistance = currentDistance * (1 - zoomAlpha * 0.6)

							local offset = Vector3.new(
								math.sin(currentAngle) * currentDistance + swayX,
								originalCameraCF.Position.Y - targetPosition.Y + swayY + verticalOffset,
								math.cos(currentAngle) * currentDistance
							)

							local newPos = targetPosition + offset

							local fovOffset = math.sin(mainAlpha * math.pi * 1.5) * 10
							local zoomFOV = math.max(originalFOV - 25, originalFOV - (zoomAlpha * 30))
							camera.FieldOfView = (originalFOV + fovOffset) * (1 - zoomAlpha) + zoomFOV * zoomAlpha

							local tiltMultiplier = (1 - zoomAlpha) * (1 - zoomAlpha)
							local tilt = CFrame.Angles(
								math.sin(mainAlpha * math.pi * 2) * 0.06 * tiltMultiplier,
								math.cos(mainAlpha * math.pi * 2.5) * 0.04 * tiltMultiplier,
								math.sin(mainAlpha * math.pi * 3) * 0.03 * tiltMultiplier
							)

							local lookOffset = Vector3.new(
								math.sin(mainAlpha * math.pi * 2) * 0.7 * (1 - zoomAlpha),
								math.cos(mainAlpha * math.pi * 2.5) * 0.4 * (1 - zoomAlpha),
								math.sin(mainAlpha * math.pi * 1.5) * 0.3 * (1 - zoomAlpha)
							)

							camera.CFrame = CFrame.lookAt(newPos, targetPosition + lookOffset) * tilt
						end)

						task.wait(totalDuration)

						local resetDuration = 1.2

						local finalTween = tweenservice:Create(camera, 
							TweenInfo.new(resetDuration, Enum.EasingStyle.Cubic, Enum.EasingDirection.InOut),
							{
								CFrame = originalCameraCF,
								FieldOfView = originalFOV
							}
						)
						finalTween:Play()

						tweenservice:Create(blur, TweenInfo.new(resetDuration, Enum.EasingStyle.Cubic), {Size = 0}):Play()

						finalTween.Completed:Wait()

						camera.CameraType = originalCameraType
						blur:Destroy()
					end)
					task.wait(0.4)

					local attack = barrage:Clone()
					attack.Parent = character
					game.Debris:AddItem(attack, 5)

					local weld = Instance.new("Weld")
					weld.Parent = workspace
					game.Debris:AddItem(weld, 5)
					weld.Part0 = attack.Box
					weld.Part1 = character.HumanoidRootPart
					weld.C0 = CFrame.new(0, 0, 5)

					coroutine.wrap(function()
						local soundIds = {
							"rbxassetid://3744367524",
							"rbxassetid://7441142253",
							"rbxassetid://7441143433",
							"rbxassetid://7441142253",
							"rbxassetid://7441143433",
							"rbxassetid://7441143109"
						}

						for i = 1, 6 do
							local sound = Instance.new("Sound")
							sound.Parent = game.Workspace 
							local randomSoundId = soundIds[math.random(1, #soundIds)]
							sound.SoundId = randomSoundId
							sound.PlayOnRemove = true
							sound.Volume = 1.5
							sound:Destroy()
							task.wait(0.1) 
						end
					end)()

					task.delay(0.6, function()
						for _, v in attack:GetDescendants() do
							if v:IsA("ParticleEmitter") then
								v.Enabled = false
							end
						end
					end)

					task.wait(0.8)
					currentAnimationTrack:Stop()

					hideDagger("Left Arm", 2)
					hideDagger("Right Arm", 2)

					local newAnimation = Instance.new("Animation")
					newAnimation.AnimationId = "rbxassetid://12460977270"
					local newAnimationTrack = animator:LoadAnimation(newAnimation)
					currentAnimationTrack = newAnimationTrack

					newAnimationTrack:Play()
					newAnimationTrack:AdjustSpeed(1.2)

					local attack = barragepunch:Clone()
					attack.Parent = workspace
					game.Debris:AddItem(attack, 5)
					attack.Part.CFrame = char.HumanoidRootPart.CFrame * CFrame.new(0, 0, -3) * CFrame.Angles(0, math.rad(90), 0)

					coroutine.wrap(function()
						local soundIds = {
							"rbxassetid://8595983255",
							"rbxassetid://8595977193",
							"rbxassetid://8595974357",
							"rbxassetid://8595975458",
							"rbxassetid://8348699396",
						}

						for i = 1, 12 do
							local sound = Instance.new("Sound")
							sound.Parent = game.Workspace 
							local randomSoundId = soundIds[math.random(1, #soundIds)]
							sound.SoundId = randomSoundId
							sound.PlayOnRemove = true
							sound.Volume = 3
							sound:Destroy()
							task.wait(0.05) 
						end
					end)()

					task.wait(0.8)
					for _, v in attack:GetDescendants() do
						if v:IsA("ParticleEmitter") then
							v.Enabled = false
						end
					end
					newAnimationTrack:Stop()

					local newAnimation = Instance.new("Animation")
					newAnimation.AnimationId = "rbxassetid://18896127525"
					local newAnimationTrack = animator:LoadAnimation(newAnimation)
					currentAnimationTrack = newAnimationTrack

					newAnimationTrack:Play()
					newAnimationTrack:AdjustSpeed(1.7)

					task.delay(0.2, function()
						local sound = Instance.new("Sound")
						sound.Parent = game.Workspace
						sound.SoundId = "rbxassetid://18179518411"
						sound.PlayOnRemove = true
						sound.Volume = 2
						sound:Destroy()
					end)
				end)()
			end


			if animationId == "rbxassetid://10468665991" then
				coroutine.wrap(function()
					task.wait()
					hideDagger("Right Arm", 1)
					currentAnimationTrack.TimePosition = 7

					task.spawn(function()
						local currentSound = nil
						if currentSound then
							currentSound:Destroy()
						end
						local sound = Instance.new("Sound")
						sound.SoundId = movevc
						sound.Parent = character.Head
						sound.Volume = 5
						sound.TimePosition = 2.2
						currentSound = sound
						sound:Play()



						task.wait(1.5)
						if sound == currentSound then
							sound:Destroy()
							currentSound = nil
						end
					end)



					task.wait(0.5)
					local pun = punch:Clone()
					pun.Anchored = true
					game.Debris:AddItem(pun, 5)
					pun.Parent = workspace
					pun.CFrame = char.HumanoidRootPart.CFrame * CFrame.new(0, 0, -5) * CFrame.Angles(0, math.rad(90), math.rad(90))
					for i, v in pun:GetDescendants() do
						if v:IsA("ParticleEmitter") then
							v:Emit(v:GetAttribute("EmitCount"))

						end
					end
				end)()
			end
			if animationId == "rbxassetid://12983333733" then -- sigmaboy
				local caught = player.Character:WaitForChild("CameraRig")
				caught.AnimationController:Destroy()
				caught.camera:Remove()
				hideDagger("Left Arm", 9)
				hideDagger("Right Arm", 9)



				local knightPositions = {
					Vector3.new(4.5, 0, -4.5), 
					Vector3.new(-4.5, 0, -4.5), 
					Vector3.new(7.5, 0, -7.5),
					Vector3.new(-7.5, 0, -7.5) 
				}

				local knights = {}

				for _, pos in ipairs(knightPositions) do
					local knight = Knight:Clone()
					knight.Parent = game.Workspace
					game.Debris:AddItem(knight, 50)


					knight.HumanoidRootPart.CFrame = player.Character.HumanoidRootPart.CFrame * CFrame.new(pos) - Vector3.new(0, 15, 0)
					knight.HumanoidRootPart.Anchored = true
					tweenservice:Create(knight.HumanoidRootPart, TweenInfo.new(1, Enum.EasingStyle.Quad, Enum.EasingDirection.Out), {CFrame = knight.HumanoidRootPart.CFrame + Vector3.new(0, 15, 0)}):Play()


					local sao = smallshadow:Clone()
					game.Debris:AddItem(sao, 50)
					sao.Parent = workspace
					sao.Anchored = true
					sao.CFrame = knight.HumanoidRootPart.CFrame + Vector3.new(0, 13, 0)

					coroutine.wrap(function()
						task.wait(6)
						local yes = bigPunch:Clone()
						yes.Parent = workspace
						yes.CFrame = knight.HumanoidRootPart.CFrame * CFrame.new(0, 0, -5)
						for i, v in yes:GetDescendants() do
							if v:IsA("ParticleEmitter") then
								v:Emit(v:GetAttribute("EmitCount"))
							end
						end
					end)()
					for i, v in sao:GetDescendants() do
						if v:IsA("ParticleEmitter") then
							v.Enabled = true
						end
					end

					coroutine.wrap(function()
						task.wait(0.5)
						for i, v in sao:GetDescendants() do
							if v:IsA("ParticleEmitter") then
								v.Enabled = false
							end
						end
					end)()
					local animation = Instance.new("Animation")
					animation.AnimationId = "rbxassetid://12983333733"

					local animTrack = knight.Humanoid:LoadAnimation(animation)
					animTrack:Play()

					table.insert(knights, knight)

					coroutine.wrap(function()
						task.wait(7.5)
						for i, v in sao:GetDescendants() do
							if v:IsA("ParticleEmitter") then
								v.Enabled = true
							end
						end
						tweenservice:Create(knight.HumanoidRootPart, TweenInfo.new(3, Enum.EasingStyle.Quad, Enum.EasingDirection.Out), {CFrame = knight.HumanoidRootPart.CFrame - Vector3.new(0, 15, 0)}):Play()
						task.wait(1)
						for i, v in sao:GetDescendants() do
							if v:IsA("ParticleEmitter") then
								v.Enabled = false
							end
						end
					end)()
				end
			end


			if animationId == "rbxassetid://12447707844" then
				coroutine.wrap(function()
					local player = game.Players.LocalPlayer
					local character = player.Character
					if not character then return end

					local humanoidRootPart = character:FindFirstChild("HumanoidRootPart")
					if not humanoidRootPart then return end

					local sound = Instance.new("Sound")
					sound.SoundId = Newost
					sound.Parent = character.Head
					sound.Looped = true
					sound.Name = "DestroyOnUltOff"
					sound.TimePosition = 0
					sound.Volume = 2
					tweenservice:Create(sound, TweenInfo.new(0.7, Enum.EasingStyle.Quad, Enum.EasingDirection.Out), {Volume = 2}):Play()
					sound:Play()





					local RunService = game:GetService("RunService")
					local TweenService = game:GetService("TweenService")

					local function createAfterImage()
						local clone = character:Clone()
						clone.Parent = workspace

						local attack = flashstep:Clone()
						attack.Parent = clone

						local weld = Instance.new("Weld")
						weld.Parent = clone
						weld.Part0 = attack
						weld.Name = "safeweld"
						weld.Part1 = clone.HumanoidRootPart
						weld.C0 = CFrame.new(0, 2.5, 0)

						task.delay(0.4, function()
							for i, v in attack:GetDescendants() do
								if v:IsA("ParticleEmitter") then
									v.Enabled = false
								end
							end
						end)

						local angle = math.rad(math.random(0, 360))
						local radius = math.random(10, 20)

						local offsetX = math.cos(angle) * radius
						local offsetZ = math.sin(angle) * radius


						local randomOffset = humanoidRootPart.CFrame * CFrame.new(offsetX, 0, offsetZ)
						clone.HumanoidRootPart.CFrame = randomOffset

						for _, v in clone:GetDescendants() do
							if v:IsA("BasePart") or v:IsA("MeshPart") then
								v.CanCollide = false
							end
						end

						task.wait()
						for i, v in clone:GetDescendants() do
							if v:IsA("Weld") and v.Name ~= "safeweld" or v.Name == "DestroyOnUltOff" then
								v:Destroy()
							end
						end

						task.wait()
						for i, v in clone:GetDescendants() do
							if v:IsA("BasePart") or v:IsA("MeshPart") then
								v.Anchored = true
							end
						end
						task.wait()



						for _, part in ipairs(clone:GetDescendants()) do
							if part:IsA("BasePart") and part.Name ~= "HumanoidRootPart" then
								local tween = TweenService:Create(part, TweenInfo.new(1, Enum.EasingStyle.Quad, Enum.EasingDirection.Out), {Transparency = 1})
								tween:Play()
								tween.Completed:Connect(function()
									clone:Destroy()
								end)
							end
						end
					end

					task.wait()
					currentAnimationTrack.TimePosition = 5
					hideDagger("Left Arm", 6)
					hideDagger("Right Arm", 6)

					local newanimation1 = Instance.new("Animation")
					newanimation1.AnimationId = "rbxassetid://112620365240235"
					local newanimationtrack1 = animator:LoadAnimation(newanimation1)
					currentAnimationTrack1 = newanimationtrack1

						local sound = Instance.new("Sound")
						sound.SoundId = jumpsfx
						sound.Parent = character.Head
						sound.Name = "DestroyOnUltOff"
						sound.TimePosition = 3
						sound.Volume = 0 
						sound.PlaybackSpeed = 0.9
						sound:Play()

						

						tweenservice:Create(sound, TweenInfo.new(0.3, Enum.EasingStyle.Quad), {Volume = 2}):Play()

						task.delay(1.5, function()
							local fadeOut = tweenservice:Create(sound, TweenInfo.new(0.6, Enum.EasingStyle.Quad), {Volume = 0})
							fadeOut:Play()
							fadeOut.Completed:Wait()
							sound:Destroy()
						end)

						task.wait(1.5)




					currentAnimationTrack:Stop(0.3) 
					newanimationtrack1:Play(0.3, 1, 1.5) 
					newanimationtrack1:AdjustSpeed(0.8)

					task.wait(0.5)

					local camera = workspace.CurrentCamera
					local originalFOV = camera.FieldOfView
					local originalCFrame = camera.CFrame

					local function shakeeeeeee(duration)
						local startTime = tick()

						game:GetService("RunService").RenderStepped:Connect(function()
							local elapsed = tick() - startTime
							if elapsed > duration then return false end

							local intensity = 1

							local shakeOffset = Vector3.new(
								math.sin(elapsed * 30) * intensity,
								math.cos(elapsed * 35) * intensity * 0.2,
								math.sin(elapsed * 25) * intensity * 0.2
							)


							camera.CFrame = camera.CFrame:Lerp(
								camera.CFrame * CFrame.new(shakeOffset), 
								0.5
							)
						end)
					end


					local attack = sprint:Clone()
					attack.Parent = workspace
					game.Debris:AddItem(attack, 8)

					task.delay(6, function()
						for i, v in attack:GetDescendants() do
							if v:IsA("ParticleEmitter") then
								v.Enabled = false
							end
						end
					end)

					local weld = Instance.new("Weld")
					weld.Parent = workspace
					game.Debris:AddItem(weld, 5)
					weld.Part0 = attack
					weld.Part1 = humanoidRootPart
					weld.C0 = CFrame.new(0, 0, 0) * CFrame.Angles(math.rad(-90), 0, math.rad(90))

					local newAnimation = Instance.new("Animation")
					newAnimation.AnimationId = "rbxassetid://18897115785"
					local newAnimationTrack = animator:LoadAnimation(newAnimation)
					currentAnimationTrack = newAnimationTrack

					task.wait(0.5)
					newanimationtrack1:Stop(0.3) 
					newAnimationTrack:Play(0.3) 
					newAnimationTrack.Priority = Enum.AnimationPriority.Action4

					local sound1 = Instance.new("Sound")
					sound1.SoundId = sfxrun
					sound1.Parent = character.Head
					sound1.Looped = true
					sound1.Name = "DestroyOnUltOff"
					sound1.TimePosition = 2
					sound1.Volume = 0
					sound1:Play()
					tweenservice:Create(sound1, TweenInfo.new(0.3, Enum.EasingStyle.Quad), {Volume = 7}):Play()

					local sound2 = Instance.new("Sound")
					sound2.SoundId = run
					sound2.Parent = character.Head
					sound2.Looped = true
					sound2.Name = "DestroyOnUltOff"
					sound2.TimePosition = 0
					sound2.Volume = 0
					sound2:Play()
					tweenservice:Create(sound2, TweenInfo.new(0.3, Enum.EasingStyle.Quad), {Volume = 2}):Play()

					local bodyVelocity = Instance.new("BodyVelocity")
					bodyVelocity.MaxForce = Vector3.new(math.huge, 0, math.huge)
					bodyVelocity.Parent = humanoidRootPart

					shakeeeeeee(4.5)

					local accelerationStart = tick()
					while tick() - accelerationStart < 0.5 do

						local progress = (tick() - accelerationStart) / 0.5
						local speedMultiplier = math.sin(progress * math.pi / 2)
						bodyVelocity.Velocity = humanoidRootPart.CFrame.LookVector * (175 * speedMultiplier)
						task.wait()
					end

					local startTime = tick()
					local lastCloneTime = tick()
					while tick() - startTime < 4 do
						if tick() - lastCloneTime >= 0.5 then
							coroutine.wrap(createAfterImage)()
							lastCloneTime = tick()
						end
						bodyVelocity.Velocity = humanoidRootPart.CFrame.LookVector * 175
						task.wait()
					end

					local newanimation2 = Instance.new("Animation")
					newanimation2.AnimationId = "rbxassetid://13876406148"
					local newanimationtrack2 = animator:LoadAnimation(newanimation2)
					currentAnimationTrack2 = newanimationtrack2

					local fadeOut1 = tweenservice:Create(sound1, TweenInfo.new(0.3, Enum.EasingStyle.Quad), {Volume = 0})
					local fadeOut2 = tweenservice:Create(sound2, TweenInfo.new(0.3, Enum.EasingStyle.Quad), {Volume = 0})
					fadeOut1:Play()
					fadeOut2:Play()
					task.wait(0.3)
					sound1:Destroy()
					sound2:Destroy()

					local sound3 = Instance.new("Sound")
					sound3.SoundId = slide
					sound3.Parent = character.Head
					sound3.Looped = true
					sound3.Name = "DestroyOnUltOff"
					sound3.TimePosition = 0.5
					sound3.Volume = 0
					sound3:Play()
					tweenservice:Create(sound3, TweenInfo.new(0.3, Enum.EasingStyle.Quad), {Volume = 5}):Play()



					local slowDownStart = tick()
					local function returnsigma()
						local returnStart = tick()
						local returnDuration = 0.8

						game:GetService("RunService").RenderStepped:Connect(function()
							local elapsed = math.min((tick() - returnStart) / returnDuration, 1)
							local alpha = 1 - (1 - elapsed) * (1 - elapsed)

							local swayAmount = math.sin(elapsed * 6) * (5 * (1 - alpha))
							camera.FieldOfView = originalFOV + (25 * (1 - alpha)) + swayAmount

							if elapsed >= 1 then 
								camera.FieldOfView = originalFOV
								return false 
							end
						end)
					end

					returnsigma()

					local auraclone = aura:Clone()
					for _, AuraPart in ipairs(auraclone:GetChildren()) do

						local CharacterPart = character:FindFirstChild(AuraPart.Name)
						if CharacterPart then
							for _, AuraItem in ipairs(AuraPart:GetChildren()) do
								AuraItem.Parent = CharacterPart
								AuraItem.Name = "DestroyOnUltOff"
								if AuraItem:IsA("ParticleEmitter") then
									AuraItem.LockedToPart = true
								end
							end
						end
					end

					newAnimationTrack:Stop(0.3) 
					newanimationtrack2:Play(0.3) 

					while tick() - slowDownStart < 0.5 do
						local progress = (tick() - slowDownStart) / 0.5
						local speedMultiplier = math.cos(progress * math.pi / 2)
						bodyVelocity.Velocity = humanoidRootPart.CFrame.LookVector * (200 * speedMultiplier)
						task.wait()
					end

					local function finalshakemybooty()
						local startTime = tick()
						local duration = 0.6

						game:GetService("RunService").RenderStepped:Connect(function()
							local elapsed = tick() - startTime
							if elapsed > duration then return false end

							local fadeOut = 1 - (elapsed / duration)
							local intensity = 2 * fadeOut

							local shakeOffset = Vector3.new(
								math.sin(elapsed * 40) * intensity,
								math.cos(elapsed * 45) * intensity * 0.05,
								math.sin(elapsed * 35) * intensity * 0.05
							)


							camera.CFrame = camera.CFrame:Lerp(
								camera.CFrame * CFrame.new(shakeOffset), 
								0.3
							)
						end)
					end



					bodyVelocity:Destroy()

					task.wait(0.9)

					finalshakemybooty()

					local sound4 = Instance.new("Sound")
					sound4.SoundId = slashsfx
					sound4.Parent = character.Head
					sound4.Looped = true
					sound4.Name = "DestroyOnUltOff"

					sound4.TimePosition = 0.3
					sound4.Volume = 0
					sound4:Play()
					tweenservice:Create(sound4, TweenInfo.new(0.3, Enum.EasingStyle.Quad), {Volume = 7}):Play()

					task.wait(0.5)
					local fadeOut3 = tweenservice:Create(sound3, TweenInfo.new(0.3, Enum.EasingStyle.Quad), {Volume = 0})
					local fadeOut4 = tweenservice:Create(sound4, TweenInfo.new(0.3, Enum.EasingStyle.Quad), {Volume = 0})
					fadeOut3:Play()
					fadeOut4:Play()
					task.wait(0.3)
					sound3:Destroy()
					sound4:Destroy()
				end)()
			end






			if animationId == "rbxassetid://10471336737" then
				coroutine.wrap(function()
					task.wait(0.4)
					local pun = kick:Clone()
					for i, v in pun:GetDescendants() do
						if v:IsA("ParticleEmitter") then
							v.Brightness = 1.5
						end
					end
					game.Debris:AddItem(pun, 5)
					pun.Parent = workspace
					pun.CFrame = char.HumanoidRootPart.CFrame * CFrame.new(0, 0, -5)
					for i, v in pun:GetDescendants() do
						if v:IsA("ParticleEmitter") then
							v:Emit(v:GetAttribute("EmitCount"))
						end
					end
				end)()
			end




			if replacementData then
				animationTrack:Stop() 

				if currentAnimationTrack then
					currentAnimationTrack:Stop()
				end

				local newAnimation = Instance.new("Animation")
				newAnimation.AnimationId = replacementData[1] 
				local newAnimationTrack = animator:LoadAnimation(newAnimation)
				currentAnimationTrack = newAnimationTrack

				newAnimationTrack:Play()
				newAnimationTrack:AdjustSpeed(replacementData[2]) 

				newAnimationTrack.Stopped:Connect(function()
					if currentAnimationTrack == newAnimationTrack then
						currentAnimationTrack = nil
					end
				end)
			end
		end

		animator.AnimationPlayed:Connect(onAnimationPlayed)
	end

	setupAnimationReplacement(animator)


	if _G.Morph == true then

		for i, v in char:GetDescendants() do
			if v.Name == "WindTrail" then
				v:Destroy()
			end
		end

		for i, v in char:GetChildren() do
			if v:IsA("CharacterMesh") then
				v:Destroy()
			end
			if v:IsA("BasePart") then
				v.Color = Color3.fromRGB(255, 204, 153)
			end
		end

		for i, v in char:GetDescendants() do
			if v:IsA("Shirt") or v:IsA("Pants") or v:IsA("Accessory") or v:IsA("Decal") or v:IsA("ShirtGraphic") then
				v:Destroy()
			end
		end

		char.Head.Mesh.Scale = Vector3.new(0, 0, 0)

		task.wait()
		local success, obj = pcall(function()
			return game:GetObjects("rbxassetid://97587542608219")[1]
		end)

		if success and obj then
			obj.Parent = char
			if obj:FindFirstChild("arm") then
				local arm2 = obj.arm:Clone()
				arm2.Parent = obj

				weldtopart("Weld", obj["head"].Handle, char.Head, CFrame.new(0, 0, 0))
				weldtopart("Weld", obj["head2"].Handle, char.Head, CFrame.new(-0.1, -0.5, 0.1))
				weldtopart("Weld", obj["torso"].Handle, char.Torso, CFrame.new(0, 0.4, -0.1))
				weldtopart("Weld", obj["arm"].Handle, char["Right Arm"], CFrame.new(0, -0.3, 0))
				weldtopart("Weld", arm2.Handle, char["Left Arm"], CFrame.new(0, -0.3, 0))

				for i, v in obj:GetChildren() do
					v.Parent = char
				end
			end
		end








		local function fixTransparency()
			while true do
				local allCorrect = false

				for _, v in char:GetDescendants() do
					if (v:IsA("Part") or v:IsA("MeshPart")) and v.Name ~= "HumanoidRootPart" and v.Name ~= "Head" then
						if v.Transparency ~= 0 then
							v.Transparency = 0
							allCorrect = true
						end
					end
				end

				if allCorrect then
					break
				end

				task.wait(0.1) 
			end
		end


		char:WaitForChild("head").Handle.Changed:Connect(function(property)
			if property == "Transparency" then
				task.spawn(fixTransparency)

			end
		end)

		char:WaitForChild("Left Arm").Changed:Connect(function(property)
			if property == "Transparency" then
				char["Right Arm"].Transparency = 0
				char["Left Arm"].Transparency = 0
			end
		end)

	end
	local playershirt = LocalPlayer.Character.Shirt

	game:GetService("RunService").Heartbeat:Connect(function()
		local rootPart = character:FindFirstChild("HumanoidRootPart")
		if rootPart then
			for _, sound in pairs(rootPart:GetChildren()) do
				if sound:IsA("Sound") and sound.SoundId == "rbxassetid://14762034452" then
					sound:Destroy()
				end
			end
		end
	end)

	workspace.Thrown.ChildAdded:Connect(function(child)
		if child.Name == "Model" and child:FindFirstChild("Shirt") then
			local childshirt = child.Shirt

			if child.Shirt.ShirtTemplate == playershirt.ShirtTemplate then
				child:FindFirstChildOfClass("Part").Transparency = 1
				child:FindFirstChildOfClass("Part"):ClearAllChildren()
			end
		end
	end)
end

local CollectionService = game:GetService("CollectionService")
local TextService = game:GetService("TextService")
local LocalPlayer = game.Players.LocalPlayer
local KJDialogueTemplate = game:GetService("ReplicatedStorage").Resources.UFW.TekrinnDialogue.KJDialogue

local function easeOutQuad(x)
    return 1 + 2.70158 * math.pow(x - 1, 3) + 1.70158 * math.pow(x - 1, 2)
end

local function getColor(t, keypoints)
    local k1 = keypoints[1]
    local k2 = keypoints[#keypoints]
    local alpha = 0.5
    local value = k1.Value
    
    for i = 1, #keypoints - 1 do
        if keypoints[i].Time <= t and t <= keypoints[i + 1].Time then
            k1 = keypoints[i]
            k2 = keypoints[i + 1]
            alpha = (t - k1.Time) / (k2.Time - k1.Time)
            return k1.Value:lerp(k2.Value, alpha)
        end
    end
    
    return value
end

local function retireTexts(frame)
    for _, v in frame:GetChildren() do
        if v.Name == "letter" then
            v:SetAttribute("Ending", true)
            game.TweenService:Create(v, TweenInfo.new(0.5, Enum.EasingStyle.Quad, Enum.EasingDirection.In), {
                Position = v.Position + UDim2.new(0, 0, 0, 50),
                TextTransparency = 1,
                TextStrokeTransparency = 1
            }):Play()
            game.Debris:AddItem(v, 0.5)
        end
    end
end

local function doText(textData, speaker)
    speaker = speaker or LocalPlayer
    local gui = LocalPlayer.PlayerGui:FindFirstChild(speaker.Name.."KJUI") or KJDialogueTemplate:Clone()
    local fullText = ""
    local totalWidth = 0
    local currentX = 0
    local typeDelay = 0

    local player = game.Players.LocalPlayer
    local lastUltValue = 0
    local isPlaying = false
    local DEBOUNCE_TIME = 2
    
    local flashGui = Instance.new("ScreenGui")
    flashGui.Name = "UltimateFlash"
    flashGui.Parent = player.PlayerGui
    
    local flashFrame = Instance.new("Frame")
    flashFrame.BackgroundColor3 = Color3.new(1, 1, 1)
    flashFrame.BackgroundTransparency = 1
    flashFrame.Size = UDim2.fromScale(2, 2)  
    flashFrame.Position = UDim2.fromScale(-0.5, -0.5) 
    flashFrame.Parent = flashGui

    local function playFlashEffect()
        flashFrame.BackgroundTransparency = 0
        
        local flashTween = game:GetService("TweenService"):Create(
            flashFrame,
            TweenInfo.new(1, Enum.EasingStyle.Quad, Enum.EasingDirection.Out),
            {BackgroundTransparency = 1}
        )
        
        flashTween:Play()
    end

    playFlashEffect()

    if not gui:GetAttribute("Created") then
        local template = gui:WaitForChild("Holder"):WaitForChild("Template")
        local holder = gui.Holder
        holder.Position = holder.Position - UDim2.new(0, 0, 0, 100 * #CollectionService:GetTagged("KJUI"))
        
        local imageLabel = template:WaitForChild("ImageLabel")
        imageLabel.Position = UDim2.new(0.5, 0, 0.5, -60)
        imageLabel.ImageTransparency = 1
        imageLabel.Image = "rbxthumb://type=Asset&id=117166026386029&w=768&h=432"
        imageLabel.ImageColor3 = Color3.fromRGB(0, 157, 255)
        
        local nameLabel = template:WaitForChild("Name")
        nameLabel.Position = UDim2.new(0.5, 0, 0.5, -35)
        nameLabel.TextTransparency = 1
        nameLabel.TextStrokeTransparency = 1
        nameLabel.TextColor3 = Color3.fromRGB(0, 157, 255)
        nameLabel.Font = Enum.Font.SourceSans

        game.TweenService:Create(imageLabel, TweenInfo.new(1, Enum.EasingStyle.Quint, Enum.EasingDirection.Out), {
            Position = UDim2.new(0.5, 0, 0.5, -60),
            ImageTransparency = 0
        }):Play()

        game.TweenService:Create(nameLabel, TweenInfo.new(1, Enum.EasingStyle.Quint, Enum.EasingDirection.Out), {
            Position = UDim2.new(0.5, 0, 0.5, -35),
            TextTransparency = 0,
            TextStrokeTransparency = 0
        }):Play()

        task.spawn(function()
            gui:SetAttribute("Created", os.clock())
            repeat task.wait() until os.clock() - gui:GetAttribute("Created") > 5 or not gui.Parent
            gui.Name = "deleting"
            retireTexts(gui.Holder.Template)
            
            local tweenInfo = TweenInfo.new(1, Enum.EasingStyle.Quint, Enum.EasingDirection.In)
            local imageLabel = template:WaitForChild("ImageLabel")
            local nameLabel = template:WaitForChild("Name")

            game.TweenService:Create(imageLabel, tweenInfo, {
                Position = UDim2.new(0.5, 0, 0.5, -160),
                ImageTransparency = 1
            }):Play()
            
            game.TweenService:Create(nameLabel, tweenInfo, {
                Position = UDim2.new(0.5, 0, 0.5, -160),
                TextTransparency = 1,
                TextStrokeTransparency = 1
            }):Play()
            
            task.delay(1, function()
                gui:Destroy()
            end)
        end)
    else
        gui:SetAttribute("Created", os.clock())
    end

    gui.Parent = LocalPlayer.PlayerGui
    gui.Enabled = true
    gui.Name = speaker.Name.."KJUI"
    gui:AddTag("KJUI")
    gui:WaitForChild("Holder"):WaitForChild("Template"):WaitForChild("Name").Text = speaker.Name

    for _, textPart in textData do
        fullText = fullText..textPart.Text
    end

    local isHigherUp = false
    for _, part in pairs(textData) do
        if part.HigherUp then
            isHigherUp = true
            game:GetService("TweenService"):Create(gui.Holder, TweenInfo.new(0.2), {
                Position = UDim2.new(0.5, 0, 0.965, 0)
            }):Play()
        end
    end

    if not isHigherUp and gui.Holder.Position ~= UDim2.new(0.5, 0, 1, 0) then
        game:GetService("TweenService"):Create(gui.Holder, TweenInfo.new(1), {
            Position = UDim2.new(0.5, 0, 1, 0)
        }):Play()
    end

    retireTexts(gui.Holder.Template)

    for _, textPart in textData do
        local chars = string.split(textPart.Text, "")
        local font = textPart.Bold and Enum.Font.SourceSansBold or textPart.Italic and Enum.Font.SourceSansItalic or Enum.Font.SourceSans
        for _, char in chars do
            totalWidth = totalWidth + TextService:GetTextSize(char, 25, font, Vector2.new(100, 100)).X
        end
    end

    for _, textPart in textData do
        local chars = string.split(textPart.Text, "")
        local font = textPart.Bold and Enum.Font.SourceSansBold or textPart.Italic and Enum.Font.SourceSansItalic or Enum.Font.SourceSans
        
        for _, char in chars do
            local textSize = TextService:GetTextSize(char, 25, font, Vector2.new(100, 100))
            local letter = Instance.new("TextLabel")
            letter.AnchorPoint = Vector2.new(0, 0.5)
            letter.Position = UDim2.new(0.5, math.floor(currentX - totalWidth/2) - 15, 0.5, -30)
            letter.Size = UDim2.new(0, textSize.X, 0, textSize.Y)
            letter.Text = char
            letter.Name = "letter"
            letter.Font = font
            letter.TextSize = 25
            letter.Parent = gui.Holder.Template
            letter.BackgroundTransparency = 1
            letter.TextStrokeColor3 = textPart.TextStrokeColor
            letter.TextStrokeTransparency = 1
            letter.TextTransparency = 1

            local finalX = math.floor(currentX - totalWidth/2) - 15
            local startingX = finalX + 100

            task.delay(typeDelay, function()
                local startTime = os.clock()
                
                repeat
                    local progress = math.min((os.clock() - startTime) / 0.35, 1)
                    local shakeProgress = math.min((os.clock() - startTime) / textPart.Shake.Lifetime, 1)
                    local shake = not textPart.Shake.Enabled and UDim2.new(0, 0, 0, 0) or 
                                UDim2.new(0, math.random(-textPart.Shake.Intensity, textPart.Shake.Intensity) * (1-shakeProgress),
                                         0, math.random(-textPart.Shake.Intensity, textPart.Shake.Intensity) * (1-shakeProgress))
                    
                    local fade = 1 - easeOutQuad(progress)
                    local currentXPos = startingX + (finalX - startingX) * easeOutQuad(progress)
                    
                    letter.TextStrokeTransparency = (1 - progress)^10
                    letter.TextTransparency = fade
                    letter.TextSize = 25 + 25 * fade
                    letter.TextColor3 = getColor(progress, textPart.Color.Keypoints)
                    letter.Position = UDim2.new(0.5, currentXPos, 0.5, -30) + shake
                    task.wait()
                until os.clock() - startTime > math.max(0.35, textPart.Shake.Lifetime) or 
                      not letter or 
                      not letter:IsDescendantOf(gui) or 
                      letter:GetAttribute("Ending")

                if letter then
                    letter.TextStrokeTransparency = 0
                    letter.TextTransparency = 0
                    letter.TextSize = 25
                    letter.TextColor3 = textPart.Color.Keypoints[#textPart.Color.Keypoints].Value
                    letter.Position = UDim2.new(0.5, finalX, 0.5, -30)
                end
            end)

            typeDelay = typeDelay + textPart.TypeSpeed
            currentX = currentX + textSize.X + 1
        end
    end
end

if not _G.JinwooUltMonitorInitialized then
    _G.JinwooUltMonitorInitialized = true
    
    task.spawn(function()
        local player = game.Players.LocalPlayer
        local lastUltValue = 0
        local isPlaying = false
        local DEBOUNCE_TIME = 2
        
        if player.PlayerGui:FindFirstChild("UltimateFlash") then
            player.PlayerGui.UltimateFlash:Destroy()
        end
        
        local flashGui = Instance.new("ScreenGui")
        flashGui.Name = "UltimateFlash"
        flashGui.Parent = player.PlayerGui
        
        local flashFrame = Instance.new("Frame")
        flashFrame.BackgroundColor3 = Color3.new(1, 1, 1)
        flashFrame.BackgroundTransparency = 1
        flashFrame.Size = UDim2.fromScale(2, 2)
        flashFrame.Position = UDim2.fromScale(-0.5, -0.5)
        flashFrame.Parent = flashGui
        
        local function playFlashEffect()
            flashFrame.BackgroundTransparency = 0
            local flashTween = game:GetService("TweenService"):Create(
                flashFrame,
                TweenInfo.new(1, Enum.EasingStyle.Quad, Enum.EasingDirection.Out),
                {BackgroundTransparency = 1}
            )
            flashTween:Play()
        end

        local dialogues = {
            {
                textData = {
                    {
                        Text = "It's ",
                        Color = ColorSequence.new({
                            ColorSequenceKeypoint.new(0, Color3.fromRGB(255, 255, 255)),
                            ColorSequenceKeypoint.new(1, Color3.fromRGB(255, 255, 255))
                        }),
                        TextStrokeColor = Color3.fromRGB(0, 0, 0),
                        Bold = false,
                        Italic = false,
                        Shake = {
                            Enabled = false,
                            Intensity = 1,
                            Lifetime = 2
                        },
                        TypeSpeed = 0.04
                    },
                    {
                        Text = "Survival of the Fittest ",
                        Color = ColorSequence.new({
                            ColorSequenceKeypoint.new(0, Color3.fromRGB(0, 157, 255)),
                            ColorSequenceKeypoint.new(1, Color3.fromRGB(0, 225, 255))
                        }),
                        TextStrokeColor = Color3.fromRGB(0, 0, 0),
                        Bold = true,
                        Italic = true,
                        Shake = {
                            Enabled = true,
                            Intensity = 2,
                            Lifetime = 1
                        },
                        TypeSpeed = 0.04
                    },
                    {
                        Text = "in this world.",
                        Color = ColorSequence.new({
                            ColorSequenceKeypoint.new(0, Color3.fromRGB(255, 255, 255)),
                            ColorSequenceKeypoint.new(1, Color3.fromRGB(255, 255, 255))
                        }),
                        TextStrokeColor = Color3.fromRGB(0, 0, 0),
                        Bold = false,
                        Italic = false,
                        Shake = {
                            Enabled = false,
                            Intensity = 1,
                            Lifetime = 2
                        },
                        TypeSpeed = 0.04
                    }
                },
                soundId = ultlines,
                timePosition = 2,
				volume = 8,
				deleteTime = 3
            },
            {
                textData = {
                    {
                        Text = "I don't even need to ",
                        Color = ColorSequence.new({
                            ColorSequenceKeypoint.new(0, Color3.fromRGB(255, 255, 255)),
                            ColorSequenceKeypoint.new(1, Color3.fromRGB(255, 255, 255))
                        }),
                        TextStrokeColor = Color3.fromRGB(0, 0, 0),
                        Bold = false,
                        Italic = false,
                        Shake = {
                            Enabled = false,
                            Intensity = 1,
                            Lifetime = 2
                        },
                        TypeSpeed = 0.04
                    },
                    {
                        Text = "GET ANGRY ",
                        Color = ColorSequence.new({
                            ColorSequenceKeypoint.new(0, Color3.fromRGB(255, 0, 0)), 
                            ColorSequenceKeypoint.new(1, Color3.fromRGB(200, 0, 0))  
                        }),
                        TextStrokeColor = Color3.fromRGB(75, 0, 0),
                        Bold = true,
                        Italic = true,
                        Shake = {
                            Enabled = true,
                            Intensity = 3,
                            Lifetime = 1
                        },
                        TypeSpeed = 0.04
                    },
                    {
                        Text = "to kill filth like you.",
                        Color = ColorSequence.new({
                            ColorSequenceKeypoint.new(0, Color3.fromRGB(255, 255, 255)),
                            ColorSequenceKeypoint.new(1, Color3.fromRGB(255, 255, 255))
                        }),
                        TextStrokeColor = Color3.fromRGB(0, 0, 0),
                        Bold = false,
                        Italic = false,
                        Shake = {
                            Enabled = false,
                            Intensity = 1,
                            Lifetime = 2
                        },
                        TypeSpeed = 0.04
                    }
                },
                soundId = dontneedtogetangry,
                timePosition = 0,
                volume = 3,
				deleteTime = 4
            }
        }
        
        local currentDialogueIndex = 1
        
        while task.wait() do
            local ultValue = player:GetAttribute("Ultimate") or 0
            
            if ultValue >= 100 and lastUltValue < 100 and not isPlaying then
                isPlaying = true
                
                playFlashEffect()
                
                local selectedDialogue = dialogues[currentDialogueIndex]
                currentDialogueIndex = currentDialogueIndex % #dialogues + 1
                
                local sound = Instance.new("Sound")
                sound.SoundId = selectedDialogue.soundId
                sound.Volume = selectedDialogue.volume
                sound.Parent = player.Character.Head
                sound.TimePosition = selectedDialogue.timePosition
                sound:Play()
                game:GetService("Debris"):AddItem(sound, selectedDialogue.deleteTime)
                
                doText(selectedDialogue.textData, player)
                
                task.delay(DEBOUNCE_TIME, function()
                    isPlaying = false
                end)
            end
            
            lastUltValue = ultValue
        end
    end)
end

Sung_Woo()

if not _G.JinwooGUIInitialized then
    _G.JinwooGUIInitialized = true
    

local Players = game:GetService("Players")
local TweenService = game:GetService("TweenService")

local StatConfig = {
    BaseWalkSpeed = 16,
    WalkSpeedMultiplier = 0.05,
    MaxSTR = 50
}

local statValues = {
    STR = 0,
    AGI = 0,
    PER = 0,
    VIT = 0,
    INT = 0
}

local availablePoints = 3  
local pointsValue = nil   

local player = game.Players.LocalPlayer
local character = player.Character or player.CharacterAdded:Wait()
local humanoid = character:WaitForChild("Humanoid")

local function saveData()
    print("Attempting to save data...")
    local data = {
        stats = statValues,
        points = availablePoints
    }
    
    local success, err = pcall(function()
        writefile("SoloLeveling_SaveData.json", game:GetService("HttpService"):JSONEncode(data))
    end)
    
    if success then
        print("Data saved successfully:", game:GetService("HttpService"):JSONEncode(data))
    else
        warn("Failed to save data:", err)
    end
end

local function loadData()
    print("Attempting to load data...")
    if isfile("SoloLeveling_SaveData.json") then
        print("Save file found!")
        local success, data = pcall(function()
            return game:GetService("HttpService"):JSONDecode(readfile("SoloLeveling_SaveData.json"))
        end)
        
        if success and data then
            print("Data loaded successfully:", game:GetService("HttpService"):JSONEncode(data))
            statValues = data.stats
            availablePoints = data.points
        
            if humanoid then
                local agiMultiplier = 1 + (statValues["AGI"] * StatConfig.WalkSpeedMultiplier)
                humanoid.WalkSpeed = StatConfig.BaseWalkSpeed * agiMultiplier
            end
            
            return true
        else
            warn("Failed to parse save data:", data)
        end
    else
        print("No save file found")
    end
    return false
end

spawn(function()
    loadData()  
    while true do
        task.wait(10) 
        saveData()    
    end
end)

spawn(function()
    while true do
        if humanoid then
            local agiMultiplier = 1 + (statValues["AGI"] * StatConfig.WalkSpeedMultiplier)
            humanoid.WalkSpeed = StatConfig.BaseWalkSpeed * agiMultiplier
        end
        task.wait(0.1)
    end
end)

humanoid.AnimationPlayed:Connect(function(track)
    if track.Animation.AnimationId == "rbxassetid://10479335397" then
        coroutine.wrap(function()
            local bodyVelocity = character.HumanoidRootPart:WaitForChild("moveme")
            if bodyVelocity then
                local connection
                connection = game:GetService("RunService").Heartbeat:Connect(function()
                    if bodyVelocity.Parent then
                        local progress = statValues["STR"] / StatConfig.MaxSTR 
                        local multiplier = 0.5 + (progress * 1) 
                        
                        bodyVelocity.Velocity = bodyVelocity.Velocity * multiplier
                    else
                        connection:Disconnect()
                    end
                end)
            end
        end)()
    end
end)

-----------------------------------SOUND-----------------------------------------------------

function GetGitSoundID(GithubSnd, SoundName)
    local fileName = "customObject_Sound_" .. tostring(SoundName) .. ".mp3"

    if not isfile(fileName) then
        game:GetService("StarterGui"):SetCore("SendNotification", {
            Title = "Downloading Sound",
            Text = "Downloading " .. SoundName .. "...",
            Duration = 3
        })
        
        local success, result = pcall(function()
            return game:HttpGet(GithubSnd)
        end)
        
        if success then
            writefile(fileName, result)
            game:GetService("StarterGui"):SetCore("SendNotification", {
                Title = "Download Complete",
                Text = SoundName .. " downloaded successfully!",
                Duration = 3
            })
        else
            game:GetService("StarterGui"):SetCore("SendNotification", {
                Title = "Download Failed",
                Text = "Failed to download " .. SoundName,
                Duration = 5
            })
            return nil
        end
    end

    return (getcustomasset or getsynasset)(fileName)
end

local dokiSounds = GetGitSoundID("https://github.com/wispwisp22/sfxxxx/raw/main/Doki%20Doki%20Literature%20Club%20GUI%20SFX.mp3", "DokiDokisounds")
local futuristicSounds = GetGitSoundID("https://github.com/wispwisp22/sfxxxx/raw/main/Futuristic%20Interface%20%20Sci%20Fi%20SOUND%20FX%20(No%20Copyright).mp3", "FuturisticSounds")
local campfireSounds = GetGitSoundID("https://github.com/wispwisp22/sfxxxx/raw/main/Campfire%20(Sound%20Effect)%204K.mp3", "CampfireSounds")
-----------------------------------GUI--------------------------------------------

local player = game.Players.LocalPlayer
local character = player.Character or player.CharacterAdded:Wait()
local humanoid = character:WaitForChild("Humanoid")


local function createDynamicParticles(parent, count)
    local particlesContainer = Instance.new("Frame")
    particlesContainer.Size = UDim2.new(1, 0, 1, 0)
    particlesContainer.BackgroundTransparency = 1
    particlesContainer.ClipsDescendants = true
    particlesContainer.Parent = parent
    
    for i = 1, count do
        spawn(function()
            while particlesContainer.Parent do
                local particle = Instance.new("Frame")
                local size = math.random(2, 4)
                particle.Size = UDim2.new(0, size, 0, size)
                
                
                local startX = math.random(0, 100) / 100
                local startY = math.random(0, 100) / 100
                particle.Position = UDim2.new(startX, 0, startY, 0)
                particle.BackgroundColor3 = Color3.fromRGB(0, 195, 255)
                particle.BackgroundTransparency = 0.8
                particle.Parent = particlesContainer

                local glow = Instance.new("ImageLabel")
                glow.Size = UDim2.new(2, 0, 2, 0)
                glow.Position = UDim2.new(-0.5, 0, -0.5, 0)
                glow.BackgroundTransparency = 1
                glow.Image = "rbxassetid://131044285"
                glow.ImageColor3 = Color3.fromRGB(0, 195, 255)
                glow.ImageTransparency = 0.9
                glow.Parent = particle

     
                local endX = math.random(0, 100) / 100
                local endY = math.random(0, 100) / 100

                local midX = (startX + endX) / 2 + (math.random(-30, 30) / 100)
                local midY = (startY + endY) / 2 + (math.random(-30, 30) / 100)


                local points = {
                    UDim2.new(startX, 0, startY, 0),
                    UDim2.new(midX, 0, midY, 0),
                    UDim2.new(endX, 0, endY, 0)
                }

                for j = 1, #points - 1 do

                    local tweenInfo = TweenInfo.new(
                        math.random(3, 5), 
                        Enum.EasingStyle.Linear
                    )
                    
                    TweenService:Create(particle, tweenInfo, {
                        Position = points[j + 1],
                        BackgroundTransparency = math.random(80, 90)/100
                    }):Play()
                    
                    wait(tweenInfo.Time)
                end

                particle:Destroy()
                wait(math.random() * 2)
            end

        end)
    end
    return particlesContainer
end

local function createDynamicBackground(parent)
    local background = Instance.new("Frame")
    background.Size = UDim2.new(1, 0, 1, 0)
    background.BackgroundColor3 = Color3.fromRGB(5, 10, 25)
    background.BackgroundTransparency = 0.1
    background.BorderSizePixel = 0
    background.Parent = parent


    local glow = Instance.new("ImageLabel")
    glow.Size = UDim2.new(1.5, 0, 1.5, 0)
    glow.Position = UDim2.new(-0.25, 0, -0.25, 0)
    glow.BackgroundTransparency = 1
    glow.Image = "rbxassetid://131044285"
    glow.ImageColor3 = Color3.fromRGB(0, 195, 255)
    glow.ImageTransparency = 0.7
    glow.Parent = background

    spawn(function()
        while background.Parent do
            TweenService:Create(glow, TweenInfo.new(2, Enum.EasingStyle.Sine, Enum.EasingDirection.InOut), {
                ImageTransparency = 0.8,
                Size = UDim2.new(1.3, 0, 1.3, 0)
            }):Play()
            wait(2)
            TweenService:Create(glow, TweenInfo.new(2, Enum.EasingStyle.Sine, Enum.EasingDirection.InOut), {
                ImageTransparency = 0.9,
                Size = UDim2.new(1.2, 0, 1.2, 0)
            }):Play()
            wait(2)
        end
    end)

    return background
end

local function createDynamicBorder(parent)
    local borders = {}
    local positions = {
        {UDim2.new(0, 0, 0, 0), UDim2.new(1, 0, 0, 2)},     -- Top border
        {UDim2.new(0, 0, 1, -2), UDim2.new(1, 0, 0, 2)},    -- Bottom border
        {UDim2.new(0, 0, 0, 0), UDim2.new(0, 2, 1, 0)},     -- Left border
        {UDim2.new(1, -2, 0, 0), UDim2.new(0, 2, 1, 0)}     -- Right border
    }

    for i, pos in ipairs(positions) do
        local border = Instance.new("Frame")
        border.Position = pos[1]
        border.Size = pos[2]
        border.BackgroundColor3 = Color3.fromRGB(0, 100, 255)
        border.BackgroundTransparency = 0.5
        border.Parent = parent
        table.insert(borders, border)

        local borderGlow = Instance.new("ImageLabel")
        if i == 1 then
            borderGlow.Size = UDim2.new(1, 0, 4, 0)
            borderGlow.Position = UDim2.new(0, 0, -1.5, 0)
        elseif i == 2 then

            borderGlow.Size = UDim2.new(1, 0, 4, 0)
            borderGlow.Position = UDim2.new(0, 0, -1, 0)
        else
            borderGlow.Size = UDim2.new(4, 0, 1, 0)

            borderGlow.Position = UDim2.new(-1.5, 0, 0, 0)
        end
        borderGlow.BackgroundTransparency = 1
        borderGlow.Image = "rbxassetid://131044285"
        borderGlow.ImageColor3 = Color3.fromRGB(0, 100, 255)
        borderGlow.ImageTransparency = 0.8
        borderGlow.Parent = border

        if i == 2 then
            local extraGlow = Instance.new("ImageLabel")

            extraGlow.Size = UDim2.new(1, 0, 4, 0)
            extraGlow.Position = UDim2.new(0, 0, -2, 0)
            extraGlow.BackgroundTransparency = 1
            extraGlow.Image = "rbxassetid://131044285"
            extraGlow.ImageColor3 = Color3.fromRGB(0, 100, 255)
            extraGlow.ImageTransparency = 0.8
            extraGlow.Parent = border
        end
    end

    spawn(function()
        while parent.Parent do
            for _, border in ipairs(borders) do
                TweenService:Create(border, TweenInfo.new(1.5, Enum.EasingStyle.Sine, Enum.EasingDirection.InOut), {
                    BackgroundTransparency = 0.3
                }):Play()
                
                for _, glow in ipairs(border:GetChildren()) do
                    if glow:IsA("ImageLabel") then
                        TweenService:Create(glow, TweenInfo.new(1.5, Enum.EasingStyle.Sine, Enum.EasingDirection.InOut), {
                            ImageTransparency = 0.7
                        }):Play()
                    end
                end
            end
            wait(1.5)
            for _, border in ipairs(borders) do
                TweenService:Create(border, TweenInfo.new(1.5, Enum.EasingStyle.Sine, Enum.EasingDirection.InOut), {
                    BackgroundTransparency = 0.7
                }):Play()
                
                for _, glow in ipairs(border:GetChildren()) do
                    if glow:IsA("ImageLabel") then
                        TweenService:Create(glow, TweenInfo.new(1.5, Enum.EasingStyle.Sine, Enum.EasingDirection.InOut), {
                            ImageTransparency = 0.9
                        }):Play()
                    end
                end
            end
            wait(1.5)
        end
    end)
end



local function createSoloLevelingNotification(message)
    local isOpen = true
    local Container = nil
    

    local guiPart = Instance.new("Part")
    guiPart.Size = Vector3.new(7.5, 5, 0.1)
    guiPart.Transparency = 0.4
    guiPart.CanCollide = false
    guiPart.Anchored = true
    guiPart.Name = "SoloLevelingGUI"
    guiPart.Material = Enum.Material.SmoothPlastic
    guiPart.Color = Color3.fromRGB(0, 10, 30)
    
   
    local glow = Instance.new("PointLight")
    glow.Color = Color3.fromRGB(0, 195, 255)
    glow.Range = 8
    glow.Brightness = 1
    glow.Parent = guiPart
    
 
    local hoverOffset = 0
    local hoverSpeed = 1
    local hoverAmplitude = 0.1
    
    local isFollowing = false
    local targetPosition = nil

    local function updatePartPosition()
        local character = player.Character
        if character and character:FindFirstChild("HumanoidRootPart") then
            local hrp = character.HumanoidRootPart
            
            hoverOffset = hoverOffset + 0.3 * game:GetService("RunService").RenderStepped:Wait()
            local hoverY = math.sin(hoverOffset) * 0.15
            

            local distance = (hrp.Position - guiPart.Position).Magnitude
            
            local targetY = hrp.Position.Y + 2 + hoverY
            
            if distance > 20 and not isFollowing then
                isFollowing = true
                targetPosition = hrp.Position + hrp.CFrame.LookVector * 3
            elseif distance < 8 and isFollowing then
                isFollowing = false
                targetPosition = guiPart.Position
            end
            
            if isFollowing then
                targetPosition = hrp.Position + hrp.CFrame.LookVector * 3
            end
            
            local speedMultiplier = math.min(1, distance / 20) 
            local lerpAlpha = 0.04 * speedMultiplier 
            

            if targetPosition then
                local currentPos = guiPart.Position
                local newPos = Vector3.new(
                    currentPos.X + (targetPosition.X - currentPos.X) * lerpAlpha,
                    targetY,
                    currentPos.Z + (targetPosition.Z - currentPos.Z) * lerpAlpha
                )

                local lookAt = hrp.Position + Vector3.new(0, 2, 0)
                local currentCFrame = guiPart.CFrame
                local targetCFrame = CFrame.new(newPos, lookAt)

                guiPart.CFrame = currentCFrame:Lerp(targetCFrame, lerpAlpha)
            end
            
            glow.Brightness = math.clamp(4 / distance, 0.4, 1)
        end
    end
    
    if player.Character and player.Character:FindFirstChild("HumanoidRootPart") then
        local hrp = player.Character.HumanoidRootPart
        
        local rightVector = hrp.CFrame.RightVector
        local forwardVector = hrp.CFrame.LookVector
        local initialPos = hrp.Position + (rightVector * 4) + (forwardVector * 5) + Vector3.new(0, 2, 0)
        guiPart.CFrame = CFrame.new(initialPos, hrp.Position + Vector3.new(0, 2, 0))
        
        isFollowing = true
        targetPosition = hrp.Position + hrp.CFrame.LookVector * 3
        hoverOffset = 0 
    end
    
    game:GetService("RunService").RenderStepped:Connect(function()
        if guiPart.Parent then
            updatePartPosition()
        end
    end)
    
    guiPart.Parent = workspace
    
    local MainGui = Instance.new("SurfaceGui")
    MainGui.Face = Enum.NormalId.Front
    MainGui.SizingMode = Enum.SurfaceGuiSizingMode.PixelsPerStud
    MainGui.PixelsPerStud = 100
    MainGui.AlwaysOnTop = true
    MainGui.Parent = guiPart
    
    Container = Instance.new("Frame")
    Container.Size = UDim2.new(1, 0, 1, 0)
    Container.Position = UDim2.new(0, 0, 0, 0)
    Container.BackgroundTransparency = 1
    Container.Parent = MainGui

    local openTween = TweenService:Create(Container, TweenInfo.new(0.6, Enum.EasingStyle.Back, Enum.EasingDirection.Out), {
        Size = UDim2.new(0, 600, 0, 350),
        Position = UDim2.new(0.5, -300, 0.5, -175)
    })
    openTween:Play()

    local dynamicBg = createDynamicBackground(Container)
    

    createDynamicParticles(Container, 15)
    

    createDynamicBorder(Container)


    local Scanlines = Instance.new("Frame")
    Scanlines.Size = UDim2.new(1, 0, 1, 0)
    Scanlines.BackgroundTransparency = 1
    Scanlines.ZIndex = 10
    Scanlines.Parent = Container


    for i = 1, 50 do
        local line = Instance.new("Frame")
        line.Size = UDim2.new(1, 0, 0, 1)
        line.Position = UDim2.new(0, 0, i/50, 0)
        line.BackgroundColor3 = Color3.fromRGB(0, 195, 255)
        line.BackgroundTransparency = 0.95
        line.Parent = Scanlines
        
        spawn(function()
            while line.Parent do
                local transparency = math.random(95, 98) / 100
                local tweenInfo = TweenInfo.new(math.random(1, 2), Enum.EasingStyle.Linear)
                local tween = TweenService:Create(line, tweenInfo, {BackgroundTransparency = transparency})
                tween:Play()
                wait(tweenInfo.Time)
            end
        end)
    end

    local Draggable = Instance.new("TextButton")
    Draggable.Size = UDim2.new(1, 0, 1, 0)
    Draggable.Position = UDim2.new(0, 0, 0, 0)
    Draggable.BackgroundTransparency = 1
    Draggable.Text = ""
    Draggable.Parent = Container
    
    local Background = Instance.new("Frame")
    Background.Size = UDim2.new(1, 0, 1, 0)
    Background.BackgroundColor3 = Color3.fromRGB(10, 15, 30)
    Background.BackgroundTransparency = 0.2
    Background.BorderSizePixel = 0
    Background.Parent = Container
    

    local function createBar(yPos)
        local Bar = Instance.new("Frame")
        Bar.Size = UDim2.new(1, 0, 0, 4)
        Bar.Position = UDim2.new(0, 0, yPos, 0)
        Bar.BackgroundColor3 = Color3.fromRGB(0, 195, 255)
        Bar.BorderSizePixel = 0
        Bar.Parent = Container
        return Bar
    end
    
    local TopBar = createBar(0)
    local BottomBar = createBar(1)
    
    local HeaderContainer = Instance.new("Frame")
    HeaderContainer.Size = UDim2.new(0, 200, 0, 30)
    HeaderContainer.Position = UDim2.new(0.05, 0, 0.05, 0)
    HeaderContainer.BackgroundTransparency = 1
    HeaderContainer.Parent = Container
    
    local IconFrame = Instance.new("Frame")
    IconFrame.Size = UDim2.new(0, 30, 0, 30)
    IconFrame.BackgroundTransparency = 1
    IconFrame.Parent = HeaderContainer
    
    local IconBorder = Instance.new("UIStroke")
    IconBorder.Color = Color3.fromRGB(0, 195, 255)
    IconBorder.Thickness = 1
    IconBorder.Parent = IconFrame
    
    local IconText = Instance.new("TextLabel")
    IconText.Size = UDim2.new(1, 0, 1, 0)
    IconText.Text = "!"
    IconText.TextColor3 = Color3.fromRGB(0, 195, 255)
    IconText.TextSize = 20
    IconText.Font = Enum.Font.GothamBold
    IconText.BackgroundTransparency = 1
    IconText.Parent = IconFrame
    
    local TitleFrame = Instance.new("Frame")
    TitleFrame.Size = UDim2.new(0, 140, 0, 30)
    TitleFrame.Position = UDim2.new(0, 40, 0, 0)
    TitleFrame.BackgroundTransparency = 1
    TitleFrame.Parent = HeaderContainer
    
    local TitleBorder = Instance.new("UIStroke")
    TitleBorder.Color = Color3.fromRGB(0, 195, 255)
    TitleBorder.Thickness = 1
    TitleBorder.Parent = TitleFrame
    
    local TitleText = Instance.new("TextLabel")
    TitleText.Size = UDim2.new(1, 0, 1, 0)
    TitleText.Text = "NOTIFICATION"
    TitleText.TextColor3 = Color3.fromRGB(0, 195, 255)
    TitleText.TextSize = 16
    TitleText.Font = Enum.Font.GothamBold
    TitleText.BackgroundTransparency = 1
    TitleText.Parent = TitleFrame
    
    local MessageText = Instance.new("TextLabel")
    MessageText.Size = UDim2.new(0.9, 0, 0.2, 0)
    MessageText.Position = UDim2.new(0.05, 0, 0.3, 0)
    MessageText.Text = message
    MessageText.TextColor3 = Color3.fromRGB(200, 220, 255)
    MessageText.TextSize = 22
    MessageText.Font = Enum.Font.GothamSemibold
    MessageText.BackgroundTransparency = 1
    MessageText.TextStrokeTransparency = 0.7
    MessageText.TextStrokeColor3 = Color3.fromRGB(0, 195, 255)
    MessageText.Parent = Container

    local TextGlow = Instance.new("ImageLabel")
    TextGlow.Size = UDim2.new(1.2, 0, 1.2, 0)
    TextGlow.Position = UDim2.new(-0.1, 0, -0.1, 0)
    TextGlow.BackgroundTransparency = 1
    TextGlow.Image = "rbxassetid://131044285"
    TextGlow.ImageColor3 = Color3.fromRGB(0, 195, 255)
    TextGlow.ImageTransparency = 0.8
    TextGlow.Parent = MessageText

    local TextGlow = Instance.new("ImageLabel")
    TextGlow.Size = UDim2.new(1.2, 0, 1.2, 0)
    TextGlow.Position = UDim2.new(-0.1, 0, -0.1, 0)
    TextGlow.BackgroundTransparency = 1
    TextGlow.Image = "rbxassetid://131044285"
    TextGlow.ImageColor3 = Color3.fromRGB(0, 195, 255)
    TextGlow.ImageTransparency = 0.8
    TextGlow.Parent = MessageText

    local Scanlines = Instance.new("Frame")
    Scanlines.Size = UDim2.new(1, 0, 1, 0)
    Scanlines.BackgroundTransparency = 1
    Scanlines.ZIndex = 10
    Scanlines.Parent = Container

    for i = 1, 50 do
        local line = Instance.new("Frame")
        line.Size = UDim2.new(1, 0, 0, 1)
        line.Position = UDim2.new(0, 0, i/50, 0)
        line.BackgroundColor3 = Color3.fromRGB(0, 195, 255)
        line.BackgroundTransparency = 0.95
        line.Parent = Scanlines
        
        spawn(function()
            while line.Parent do
                local transparency = math.random(95, 98) / 100
                local tweenInfo = TweenInfo.new(math.random(1, 2), Enum.EasingStyle.Linear)
                local tween = TweenService:Create(line, tweenInfo, {BackgroundTransparency = transparency})
                tween:Play()
                wait(tweenInfo.Time)
            end
        end)
    end

    local function createDistortionLine()
        local line = Instance.new("Frame")
        line.Size = UDim2.new(1, 0, 0, math.random(1, 3))
        line.Position = UDim2.new(0, 0, math.random(), 0)
        line.BackgroundColor3 = Color3.fromRGB(0, 195, 255)
        line.BackgroundTransparency = 0.7
        line.Parent = Container
        
        spawn(function()
            local duration = math.random(10, 20) / 100
            wait(duration)
            line:Destroy()
        end)
    end

    TitleText.TextSize = 20
    TitleText.Font = Enum.Font.GothamBold
    TitleText.TextStrokeTransparency = 0.8
    TitleText.TextStrokeColor3 = Color3.fromRGB(0, 195, 255)

    local TitleGlow = TextGlow:Clone()
    TitleGlow.Parent = TitleText

    local ButtonsContainer = Instance.new("Frame")
    ButtonsContainer.Size = UDim2.new(0.8, 0, 0.15, 0)
    ButtonsContainer.Position = UDim2.new(0.1, 0, 0.7, 0)
    ButtonsContainer.BackgroundTransparency = 1
    ButtonsContainer.Parent = Container

    local ambienceSound = Instance.new("Sound")
    ambienceSound.Name = "AmbienceSound"
    ambienceSound.SoundId = futuristicSounds
    ambienceSound.Volume = 0
    ambienceSound.Looped = true
    ambienceSound.Parent = guiPart


    ambienceSound:Play()
    TweenService:Create(ambienceSound, TweenInfo.new(0.5), {Volume = 0.1}):Play()

    local buttonSound = Instance.new("Sound")
    buttonSound.Name = "ButtonSound"
    buttonSound.SoundId = dokiSounds
    buttonSound.Volume = 0.5
    buttonSound.Parent = guiPart

    local function createButton(text, position)
        local Button = Instance.new("TextButton")
        Button.Size = UDim2.new(0.4, 0, 1, 0)
        Button.Position = position
        Button.BackgroundColor3 = Color3.fromRGB(0, 195, 255)
        Button.BackgroundTransparency = 0.8
        Button.Text = text
        Button.TextColor3 = Color3.fromRGB(255, 255, 255)
        Button.TextSize = 18
        Button.Font = Enum.Font.GothamBold
        Button.Parent = ButtonsContainer
        Button.AutoButtonColor = true  
        Button.ClipsDescendants = true
        
        Button.MouseEnter:Connect(function()
            TweenService:Create(Button, TweenInfo.new(0.3), {BackgroundTransparency = 0.5}):Play()
            
            local hoverSound = Instance.new("Sound")
            hoverSound.SoundId = dokiSounds
            hoverSound.TimePosition = 1.2
            hoverSound.Volume = 0.5
            hoverSound.Parent = guiPart
            hoverSound:Play()
            
            task.delay(1, function()
                hoverSound:Destroy()
            end)
        end)
        
        Button.MouseLeave:Connect(function()
            TweenService:Create(Button, TweenInfo.new(0.3), {BackgroundTransparency = 0.8}):Play()
        end)
        
        Button.MouseButton1Click:Connect(function()
            local clickSound = Instance.new("Sound")
            clickSound.SoundId = dokiSounds
            clickSound.TimePosition = 2.6
            clickSound.Volume = 0.5
            clickSound.Parent = guiPart
            clickSound:Play()
            
            task.delay(1, function()
                clickSound:Destroy()
            end)
            
            local clickEffect = game:GetService("TweenService"):Create(Button,
                TweenInfo.new(0.1),
                {BackgroundTransparency = 0.4}
            )
            clickEffect:Play()
            clickEffect.Completed:Wait()
            game:GetService("TweenService"):Create(Button,
                TweenInfo.new(0.1),
                {BackgroundTransparency = 0.8}
            ):Play()
        end)
        
        return Button
    end

    local YesButton = createButton("ACCEPT", UDim2.new(0, 0, 0, 0))
    local NoButton = createButton("DECLINE", UDim2.new(0.6, 0, 0, 0))

    local function closeNotification()
        TweenService:Create(ambienceSound, TweenInfo.new(0.5), {Volume = 0}):Play()
        local closeTween = TweenService:Create(Container, TweenInfo.new(0.4, Enum.EasingStyle.Back, Enum.EasingDirection.In), {
            Size = UDim2.new(0, 600, 0, 0),
            Position = UDim2.new(0.5, -300, 0.5, 0)
        })
        closeTween.Completed:Connect(function()
            ambienceSound:Stop()
            MainGui:Destroy()
        end)
        closeTween:Play()
    end



local function createLevelingScreen()
    local mainFrame = Instance.new("Frame")
    mainFrame.Size = UDim2.new(1, 0, 1, 0)
    mainFrame.BackgroundTransparency = 1
    mainFrame.Parent = Container

    createDynamicBackground(mainFrame)
    createDynamicBorder(mainFrame)
    createDynamicParticles(mainFrame, 5)

    loadData()
    
    local Scanlines = Instance.new("Frame")
    Scanlines.Size = UDim2.new(1, 0, 1, 0)
    Scanlines.BackgroundTransparency = 1
    Scanlines.ZIndex = 10
    Scanlines.Parent = mainFrame

    for i = 1, 50 do
        local line = Instance.new("Frame")
        line.Size = UDim2.new(1, 0, 0, 1)
        line.Position = UDim2.new(0, 0, i/50, 0)
        line.BackgroundColor3 = Color3.fromRGB(0, 195, 255)
        line.BackgroundTransparency = 0.95
        line.Parent = Scanlines
        
        spawn(function()
            while line.Parent do
                local transparency = math.random(95, 98) / 100
                local tweenInfo = TweenInfo.new(math.random(1, 2), Enum.EasingStyle.Linear)
                local tween = TweenService:Create(line, tweenInfo, {BackgroundTransparency = transparency})
                tween:Play()
                wait(tweenInfo.Time)
            end
        end)
    end

    local background = Instance.new("Frame")
    background.Size = UDim2.new(1, 0, 1, 0)
    background.BackgroundColor3 = Color3.fromRGB(10, 15, 30)
    background.BackgroundTransparency = 0.2
    background.BorderSizePixel = 0

    background.Parent = mainFrame

    local glowEffect = Instance.new("ImageLabel")
    glowEffect.Size = UDim2.new(1.2, 0, 1.2, 0)
    glowEffect.Position = UDim2.new(-0.1, 0, -0.1, 0)
    glowEffect.BackgroundTransparency = 1
    glowEffect.Image = "rbxassetid://131044285"
    glowEffect.ImageColor3 = Color3.fromRGB(0, 195, 255)
    glowEffect.ImageTransparency = 0.9
    glowEffect.Parent = background

    local dynamicBg = createDynamicBackground(mainFrame)
    

    createDynamicParticles(mainFrame, 20)
    

    createDynamicBorder(mainFrame)


    local function createDistortionLine()
        local line = Instance.new("Frame")

        line.Size = UDim2.new(1, 0, 0, 2)
        line.Position = UDim2.new(0, 0, math.random(), 0)
        line.BackgroundColor3 = Color3.fromRGB(0, 195, 255)
        line.BackgroundTransparency = 0.7
        line.Parent = mainFrame
        

        local glow = Instance.new("ImageLabel")
        glow.Size = UDim2.new(1, 0, 3, 0)
        glow.Position = UDim2.new(0, 0, -1, 0)
        glow.BackgroundTransparency = 1
        glow.Image = "rbxassetid://131044285"

        glow.ImageColor3 = Color3.fromRGB(0, 195, 255)
        glow.ImageTransparency = 0.7
        glow.Parent = line
        
 
        spawn(function()
            local tweenInfo = TweenInfo.new(0.3, Enum.EasingStyle.Linear)
            TweenService:Create(line, tweenInfo, {BackgroundTransparency = 1}):Play()
            TweenService:Create(glow, tweenInfo, {ImageTransparency = 1}):Play()
            wait(0.3)
            line:Destroy()
        end)
    end

    spawn(function()
        while mainFrame.Parent do
            if math.random() < 0.2 then
                createDistortionLine()
            end
            wait(0.1)

        end
    end)

        local topContainer = Instance.new("Frame")
        topContainer.Size = UDim2.new(0.9, 0, 0.15, 0)
        topContainer.Position = UDim2.new(0.05, 0, 0.05, 0)
        topContainer.BackgroundTransparency = 0.9


        topContainer.BackgroundColor3 = Color3.fromRGB(0, 10, 30)
        topContainer.Parent = mainFrame

        local topBorder = Instance.new("UIStroke")
        topBorder.Color = Color3.fromRGB(0, 195, 255)
        topBorder.Thickness = 1
        topBorder.Transparency = 0.5
        topBorder.Parent = topContainer

        local function createStatusBar(icon, value, maxValue, xPos, barColor)
            local barContainer = Instance.new("Frame")

            barContainer.Size = UDim2.new(0.45, 0, 0.4, 0)
            barContainer.Position = UDim2.new(xPos, 0, 0.3, 0)
            barContainer.BackgroundTransparency = 1
            barContainer.Parent = topContainer

            local iconContainer = Instance.new("Frame")
            iconContainer.Size = UDim2.new(0.1, 0, 1, 0)
            iconContainer.BackgroundTransparency = 0.8
            iconContainer.BackgroundColor3 = barColor
            iconContainer.Parent = barContainer

            local iconText = Instance.new("TextLabel")
            iconText.Size = UDim2.new(1, 0, 1, 0)
            iconText.BackgroundTransparency = 1
            iconText.Text = icon
            iconText.TextColor3 = barColor
            iconText.TextSize = 14
            iconText.Font = Enum.Font.GothamBold
            iconText.Parent = iconContainer

            local barBg = Instance.new("Frame")
            barBg.Size = UDim2.new(0.85, 0, 0.4, 0)
            barBg.Position = UDim2.new(0.15, 0, 0.2, 0)
            barBg.BackgroundColor3 = Color3.fromRGB(0, 20, 40)
            barBg.BorderSizePixel = 0
            barBg.Parent = barContainer


            local barFill = Instance.new("Frame")
            barFill.Size = UDim2.new(value/maxValue, 0, 1, 0)
            barFill.BackgroundColor3 = barColor
            barFill.BorderSizePixel = 0
            barFill.Parent = barBg

            local valueText = Instance.new("TextLabel")
            valueText.Size = UDim2.new(0.85, 0, 0.3, 0)
            valueText.Position = UDim2.new(0.15, 0, 0.7, 0)
            valueText.BackgroundTransparency = 1
            valueText.Text = value.."/"..maxValue

            valueText.TextColor3 = Color3.fromRGB(255, 255, 255)
            valueText.TextSize = 14
            valueText.Font = Enum.Font.GothamMedium
            valueText.Parent = barContainer

            if icon == "HP" then
                local currentHealth = humanoid.Health
                local maxHealth = humanoid.MaxHealth
                

                barFill.Size = UDim2.new(currentHealth/maxHealth, 0, 1, 0)
                valueText.Text = math.floor(currentHealth).."/"..math.floor(maxHealth)
                

                humanoid.HealthChanged:Connect(function(health)
                    TweenService:Create(barFill, TweenInfo.new(0.3), {
                        Size = UDim2.new(health/maxHealth, 0, 1, 0),
                    }):Play()

                    valueText.Text = math.floor(health).."/"..math.floor(maxHealth)


                end)
            end

            if icon == "LV" then
                value = 0
                maxValue = 100
                valueText.Text = "0/" .. maxValue

            end

            return barContainer
        end

        createStatusBar("HP", humanoid.Health, humanoid.MaxHealth, 0.02, Color3.fromRGB(255, 75, 75))    -- Health
        createStatusBar("LV", 0, 100, 0.52, Color3.fromRGB(75, 150, 255))       -- Level


        local statsContainer = Instance.new("Frame")
        statsContainer.Size = UDim2.new(0.9, 0, 0.7, 0)
        statsContainer.Position = UDim2.new(0.05, 0, 0.25, 0)
        statsContainer.BackgroundTransparency = 0.9

        statsContainer.BackgroundColor3 = Color3.fromRGB(0, 10, 30)
        statsContainer.Parent = mainFrame

        local statsBorder = Instance.new("UIStroke")
        statsBorder.Color = Color3.fromRGB(0, 195, 255)
        statsBorder.Thickness = 1
        statsBorder.Transparency = 0.5
        statsBorder.Parent = statsContainer

        local upgradeButtons = {}
        local lastKillCount = 0
        local currentLevel = 0
        local killsPerLevel = 5
        local maxLevel = 100
        
        local function updatePointsDisplay()
            if pointsValue then
                pointsValue.Text = tostring(availablePoints)
                
                for _, button in pairs(upgradeButtons or {}) do
                    if availablePoints == 0 then
                        TweenService:Create(button, TweenInfo.new(0.3), {
                            BackgroundTransparency = 0.95,
                            TextTransparency = 0.5
                        }):Play()
                    else
                        TweenService:Create(button, TweenInfo.new(0.3), {
                            BackgroundTransparency = 0.8,
                            TextTransparency = 0
                        }):Play()
                    end
                end
            end
        end

        local pointsContainer = Instance.new("Frame")
        pointsContainer.Size = UDim2.new(0.45, 0, 0.12, 0)
        pointsContainer.Position = UDim2.new(0.5, 0, 0.39, 0)
        pointsContainer.BackgroundTransparency = 0.9

        pointsContainer.BackgroundColor3 = Color3.fromRGB(0, 195, 255)
        pointsContainer.Parent = statsContainer

        local pointsText = Instance.new("TextLabel")
        pointsText.Size = UDim2.new(0.7, 0, 1, 0)
        pointsText.BackgroundTransparency = 1
        pointsText.Text = "Available Points"
        pointsText.TextColor3 = Color3.fromRGB(255, 255, 255)
        pointsText.TextSize = 16
        pointsText.Font = Enum.Font.GothamMedium
        pointsText.TextXAlignment = Enum.TextXAlignment.Left
        pointsText.Position = UDim2.new(0.05, 0, 0, 0)
        pointsText.Parent = pointsContainer

        pointsValue = Instance.new("TextLabel")
        pointsValue.Size = UDim2.new(0.2, 0, 1, 0)
        pointsValue.Position = UDim2.new(0.75, 0, 0, 0)
        pointsValue.BackgroundTransparency = 1
        pointsValue.Text = tostring(availablePoints)

        pointsValue.TextColor3 = Color3.fromRGB(255, 255, 255)
        pointsValue.TextSize = 18
        pointsValue.Font = Enum.Font.GothamBold
        pointsValue.TextXAlignment = Enum.TextXAlignment.Center
        pointsValue.Parent = pointsContainer

        local function createStat(name, fullName, value, xPos, yPos, iconColor, pointsValue)
            local statContainer = Instance.new("Frame")

            statContainer.Size = UDim2.new(0.45, 0, 0.12, 0)
            statContainer.Position = UDim2.new(xPos, 0, yPos, 0)
            statContainer.BackgroundTransparency = 0.95
            statContainer.BackgroundColor3 = Color3.fromRGB(0, 195, 255)
            statContainer.Parent = statsContainer

            local nameContainer = Instance.new("Frame")
            nameContainer.Size = UDim2.new(0.12, 0, 1, 0)
            nameContainer.BackgroundColor3 = iconColor
            nameContainer.BackgroundTransparency = 0.7
            nameContainer.Parent = statContainer


            local nameText = Instance.new("TextLabel")
            nameText.Size = UDim2.new(1, 0, 1, 0)
            nameText.BackgroundTransparency = 1
            nameText.Text = name
            nameText.TextColor3 = iconColor
            nameText.TextSize = 14
            nameText.Font = Enum.Font.GothamBold
            nameText.Parent = nameContainer

            local fullNameLabel = Instance.new("TextLabel")
            fullNameLabel.Size = UDim2.new(0.4, 0, 1, 0)
            fullNameLabel.Position = UDim2.new(0.15, 0, 0, 0)
            fullNameLabel.BackgroundTransparency = 1
            fullNameLabel.Text = fullName

            fullNameLabel.TextColor3 = Color3.fromRGB(255, 255, 255)
            fullNameLabel.TextSize = 16
            fullNameLabel.Font = Enum.Font.GothamSemibold
            fullNameLabel.TextXAlignment = Enum.TextXAlignment.Left
            fullNameLabel.Parent = statContainer

            local valueLabel = Instance.new("TextLabel")
            valueLabel.Size = UDim2.new(0.15, 0, 1, 0)
            valueLabel.Position = UDim2.new(0.6, 0, 0, 0)
            valueLabel.BackgroundTransparency = 1

            valueLabel.Text = tostring(statValues[name])
            valueLabel.TextColor3 = iconColor
            valueLabel.TextSize = 18
            valueLabel.Font = Enum.Font.GothamBold
            valueLabel.Parent = statContainer


            local upgradeButton = Instance.new("TextButton")
            upgradeButton.Size = UDim2.new(0.12, 0, 0.8, 0)
            upgradeButton.Position = UDim2.new(0.85, 0, 0.1, 0)
            upgradeButton.BackgroundTransparency = 0.8
            upgradeButton.BackgroundColor3 = iconColor
            upgradeButton.Text = "+"
            upgradeButton.TextColor3 = Color3.fromRGB(255, 255, 255)
            upgradeButton.TextSize = 18
            upgradeButton.Font = Enum.Font.GothamBold
            upgradeButton.Parent = statContainer
            upgradeButton.AutoButtonColor = true  
            upgradeButton.ClipsDescendants = true  

            table.insert(upgradeButtons, upgradeButton)


            upgradeButton.MouseButton1Click:Connect(function()
                if availablePoints > 0 then
                    print("Upgrade button clicked for", name) 
                    
                    local clickEffect = game:GetService("TweenService"):Create(upgradeButton,
                        TweenInfo.new(0.1),
                        {BackgroundTransparency = 0.4}
                    )

                    clickEffect:Play()
                    
                    statValues[name] = statValues[name] + 1
                    valueLabel.Text = tostring(statValues[name])
                    
                    availablePoints = availablePoints - 1
                    updatePointsDisplay()
                    
                    local clickSound = Instance.new("Sound")
                    clickSound.SoundId = dokiSounds
                    clickSound.TimePosition = 2.6
                    clickSound.Volume = 0.5
                    clickSound.Parent = guiPart

                    clickSound:Play()
                    
                    task.delay(1, function()
                        clickSound:Destroy()
                    end)
                    
                    clickEffect.Completed:Wait()

                    if name == "AGI" then
                        if humanoid then
                            local agiMultiplier = 1 + (statValues["AGI"] * StatConfig.WalkSpeedMultiplier)
                            humanoid.WalkSpeed = StatConfig.BaseWalkSpeed * agiMultiplier
                        end
                    end

                    print("About to save data...") 
                    print("Save data called") 
                end
            end)

            upgradeButton.MouseEnter:Connect(function()
                if availablePoints > 0 then
                    game:GetService("TweenService"):Create(upgradeButton, 
                        TweenInfo.new(0.2), 
                        {BackgroundTransparency = 0.6}
                    ):Play()
                end
            end)

            upgradeButton.MouseLeave:Connect(function()
                if availablePoints > 0 then
                    game:GetService("TweenService"):Create(upgradeButton, 
                    TweenInfo.new(0.2), 
                    {BackgroundTransparency = 0.8}
                ):Play()
                end
            end)

            local infoButton = Instance.new("TextButton")
            infoButton.Size = UDim2.new(0.05, 0, 0.8, 0)
            infoButton.Position = UDim2.new(0.75, 0, 0.1, 0)
            infoButton.BackgroundTransparency = 0.8
            infoButton.BackgroundColor3 = iconColor
            infoButton.Text = "?"
            infoButton.TextColor3 = Color3.fromRGB(255, 255, 255)
            infoButton.TextSize = 14
            infoButton.Font = Enum.Font.GothamBold
            infoButton.Parent = statContainer

            local tooltipContainer = Instance.new("Frame")
            tooltipContainer.Size = UDim2.new(0, 400, 0, 200)  
            tooltipContainer.Position = UDim2.new(0.5, -200, 0.5, -100)  
            tooltipContainer.BackgroundColor3 = Color3.fromRGB(5, 10, 25)
            tooltipContainer.BackgroundTransparency = 0.1
            tooltipContainer.Visible = false
            tooltipContainer.ZIndex = 10  
            tooltipContainer.Parent = mainFrame 

            local tooltipTitle = Instance.new("TextLabel")
            tooltipTitle.Size = UDim2.new(1, 0, 0.2, 0)  
            tooltipTitle.BackgroundTransparency = 1
            tooltipTitle.Text = fullName
            tooltipTitle.TextColor3 = iconColor
            tooltipTitle.TextSize = 24  
            tooltipTitle.Font = Enum.Font.GothamBold
            tooltipTitle.ZIndex = 11
            tooltipTitle.Parent = tooltipContainer

            local tooltipDesc = Instance.new("TextLabel")
            tooltipDesc.Size = UDim2.new(0.9, 0, 0.7, 0)  
            tooltipDesc.Position = UDim2.new(0.05, 0, 0.25, 0)
            tooltipDesc.BackgroundTransparency = 1
            tooltipDesc.TextColor3 = Color3.fromRGB(200, 220, 255)
            tooltipDesc.TextSize = 20  
            tooltipDesc.Font = Enum.Font.GothamMedium
            tooltipDesc.TextWrapped = true
            tooltipDesc.TextXAlignment = Enum.TextXAlignment.Left
            tooltipDesc.ZIndex = 11
            tooltipDesc.Parent = tooltipContainer

            local closeButton = Instance.new("TextButton")
            closeButton.Size = UDim2.new(0.1, 0, 0.15, 0)
            closeButton.Position = UDim2.new(0.85, 0, 0.05, 0)
            closeButton.BackgroundTransparency = 0.8
            closeButton.BackgroundColor3 = Color3.fromRGB(255, 75, 75)
            closeButton.Text = "X"
            closeButton.TextColor3 = Color3.fromRGB(255, 255, 255)
            closeButton.TextSize = 18
            closeButton.Font = Enum.Font.GothamBold
            closeButton.ZIndex = 11
            closeButton.Parent = tooltipContainer
            closeButton.AutoButtonColor = true  
            closeButton.ClipsDescendants = true 

            closeButton.MouseEnter:Connect(function()
                TweenService:Create(closeButton, TweenInfo.new(0.2), {
                    BackgroundTransparency = 0.6
                }):Play()
            end)

            closeButton.MouseLeave:Connect(function()
                TweenService:Create(closeButton, TweenInfo.new(0.2), {
                    BackgroundTransparency = 0.8
                }):Play()
            end)

            local dimBackground = Instance.new("Frame")
            dimBackground.Size = UDim2.new(1, 0, 1, 0)
            dimBackground.Position = UDim2.new(0, 0, 0, 0)
            dimBackground.BackgroundColor3 = Color3.fromRGB(0, 0, 0)
            dimBackground.BackgroundTransparency = 1
            dimBackground.ZIndex = 9
            dimBackground.Visible = false
            dimBackground.Parent = mainFrame

            local descriptions = {
                STR = "Increases dash speed and power.\n\nBase Effect:\n• +2% dash speed per point\n• Improves dash damage\n\nSpecial Effects:\n• Every 10 points grants bonus dash distance\n• Maximum bonus at 50 points",
                AGI = "Increases movement speed and agility.\n\nBase Effect:\n• +5% movement speed per point\n• Improves dodge chance\n\nSpecial Effects:\n• Every 10 points reduces skill cooldowns\n• Maximum bonus at 50 points",
                PER = "Increases accuracy and critical hits.\n\nBase Effect:\n• +1% critical hit chance per point\n• Improves accuracy\n\nSpecial Effects:\n• Every 10 points increases critical damage\n• Maximum bonus at 50 points",
                VIT = "Increases health and defense.\n\nBase Effect:\n• +2% max health per point\n• Improves defense\n\nSpecial Effects:\n• Every 10 points grants health regeneration\n• Maximum bonus at 50 points",
                INT = "Increases mana and skill power.\n\nBase Effect:\n• +3% skill damage per point\n• Improves mana pool\n\nSpecial Effects:\n• Every 10 points reduces mana costs\n• Maximum bonus at 50 points"
            }
            tooltipDesc.Text = descriptions[name]

            local isTooltipVisible = false
            local function toggleTooltip(show)
                isTooltipVisible = show
                
                if show then
                    dimBackground.Visible = true
                    tooltipContainer.Visible = true
                    tooltipContainer.Size = UDim2.new(0, 400, 0, 0)
                    
                    TweenService:Create(dimBackground, TweenInfo.new(0.3), {
                        BackgroundTransparency = 0.5
                    }):Play()
                    
                    TweenService:Create(tooltipContainer, TweenInfo.new(0.3, Enum.EasingStyle.Back, Enum.EasingDirection.Out), {
                        Size = UDim2.new(0, 400, 0, 200)
                    }):Play()
                    
                    local clickSound = Instance.new("Sound")
                    clickSound.SoundId = dokiSounds
                    clickSound.TimePosition = 2.6
                    clickSound.Volume = 0.5
                    clickSound.Parent = guiPart
                    clickSound:Play()
                    game.Debris:AddItem(clickSound, 1)
                else
                    TweenService:Create(dimBackground, TweenInfo.new(0.2), {
                        BackgroundTransparency = 1
                    }):Play()
                    
                    TweenService:Create(tooltipContainer, TweenInfo.new(0.2, Enum.EasingStyle.Back, Enum.EasingDirection.In), {
                        Size = UDim2.new(0, 400, 0, 0)
                    }):Play()
                    
                    wait(0.2)
                    tooltipContainer.Visible = false
                    dimBackground.Visible = false
                end
            end

            infoButton.MouseButton1Click:Connect(function()
                toggleTooltip(not isTooltipVisible)
            end)

            closeButton.MouseButton1Click:Connect(function()
                toggleTooltip(false)
            end)

            dimBackground.InputBegan:Connect(function(input)
                if input.UserInputType == Enum.UserInputType.MouseButton1 then
                    toggleTooltip(false)
                end
            end)

            return statContainer
        end

        createStat("STR", "Strength", "0", 0.05, 0.05, Color3.fromRGB(255, 75, 75), pointsValue)
        createStat("AGI", "Agility", "0", 0.05, 0.22, Color3.fromRGB(75, 255, 75), pointsValue)
        createStat("PER", "Perception", "0", 0.05, 0.39, Color3.fromRGB(255, 200, 75), pointsValue)
        createStat("VIT", "Vitality", "0", 0.5, 0.05, Color3.fromRGB(75, 255, 150), pointsValue)
        createStat("INT", "Intelligence", "0", 0.5, 0.22, Color3.fromRGB(75, 150, 255), pointsValue)

        local function createStatusInfo()
            local rankTitleContainer = Instance.new("Frame")
            rankTitleContainer.Size = UDim2.new(0.9, 0, 0.08, 0)

            rankTitleContainer.Position = UDim2.new(0.05, 0, 0.65, 0)
            rankTitleContainer.BackgroundTransparency = 0.95
            rankTitleContainer.BackgroundColor3 = Color3.fromRGB(0, 10, 30)
            rankTitleContainer.Parent = mainFrame

            local rankLabel = Instance.new("TextLabel")
            rankLabel.Size = UDim2.new(0.15, 0, 1, 0)
            rankLabel.Position = UDim2.new(0.08, 0, 0, 0)
            rankLabel.BackgroundTransparency = 1
            rankLabel.Text = "RANK"

            rankLabel.TextColor3 = Color3.fromRGB(150, 150, 150)
            rankLabel.TextSize = 16
            rankLabel.Font = Enum.Font.GothamMedium
            rankLabel.TextXAlignment = Enum.TextXAlignment.Left
            rankLabel.Parent = rankTitleContainer

            local rankValue = Instance.new("TextLabel")
            rankValue.Size = UDim2.new(0.3, 0, 1, 0)
            rankValue.Position = UDim2.new(0.2, 0, 0, 0)
            rankValue.BackgroundTransparency = 1
            rankValue.Text = "E-RANK HUNTER"

            rankValue.TextColor3 = Color3.fromRGB(0, 195, 255)
            rankValue.TextSize = 16
            rankValue.Font = Enum.Font.GothamBold
            rankValue.TextXAlignment = Enum.TextXAlignment.Left
            rankValue.Parent = rankTitleContainer

            local titleLabel = Instance.new("TextLabel")
            titleLabel.Size = UDim2.new(0.15, 0, 1, 0)
            titleLabel.Position = UDim2.new(0.55, 0, 0, 0)
            titleLabel.BackgroundTransparency = 1
            titleLabel.Text = "TITLE"

            titleLabel.TextColor3 = Color3.fromRGB(150, 150, 150)
            titleLabel.TextSize = 16
            titleLabel.Font = Enum.Font.GothamMedium
            titleLabel.TextXAlignment = Enum.TextXAlignment.Left
            titleLabel.Parent = rankTitleContainer

            local titleValue = Instance.new("TextLabel")
            titleValue.Size = UDim2.new(0.3, 0, 1, 0)
            titleValue.Position = UDim2.new(0.67, 0, 0, 0)
            titleValue.BackgroundTransparency = 1
            titleValue.Text = "THE WEAKEST HUNTER"

            titleValue.TextColor3 = Color3.fromRGB(255, 75, 75)
            titleValue.TextSize = 16
            titleValue.Font = Enum.Font.GothamBold
            titleValue.TextXAlignment = Enum.TextXAlignment.Left
            titleValue.Parent = rankTitleContainer

            local classStatusContainer = Instance.new("Frame")
            classStatusContainer.Size = UDim2.new(0.9, 0, 0.08, 0)
            classStatusContainer.Position = UDim2.new(0.05, 0, 0.75, 0)
            classStatusContainer.BackgroundTransparency = 0.95

            classStatusContainer.BackgroundColor3 = Color3.fromRGB(0, 10, 30)
            classStatusContainer.Parent = mainFrame

            local classLabel = Instance.new("TextLabel")
            classLabel.Size = UDim2.new(0.15, 0, 1, 0)
            classLabel.Position = UDim2.new(0.08, 0, 0, 0)
            classLabel.BackgroundTransparency = 1
            classLabel.Text = "CLASS"

            classLabel.TextColor3 = Color3.fromRGB(150, 150, 150)
            classLabel.TextSize = 16
            classLabel.Font = Enum.Font.GothamMedium
            classLabel.TextXAlignment = Enum.TextXAlignment.Left
            classLabel.Parent = classStatusContainer

            local classValue = Instance.new("TextLabel")
            classValue.Size = UDim2.new(0.3, 0, 1, 0)
            classValue.Position = UDim2.new(0.2, 0, 0, 0)
            classValue.BackgroundTransparency = 1
            classValue.Text = "NONE"

            classValue.TextColor3 = Color3.fromRGB(180, 100, 255)
            classValue.TextSize = 16
            classValue.Font = Enum.Font.GothamBold
            classValue.TextXAlignment = Enum.TextXAlignment.Left
            classValue.Parent = classStatusContainer

            local statusLabel = Instance.new("TextLabel")
            statusLabel.Size = UDim2.new(0.15, 0, 1, 0)
            statusLabel.Position = UDim2.new(0.55, 0, 0, 0)
            statusLabel.BackgroundTransparency = 1
            statusLabel.Text = "STATUS"

            statusLabel.TextColor3 = Color3.fromRGB(150, 150, 150)
            statusLabel.TextSize = 16
            statusLabel.Font = Enum.Font.GothamMedium
            statusLabel.TextXAlignment = Enum.TextXAlignment.Left
            statusLabel.Parent = classStatusContainer

            local statusValue = Instance.new("TextLabel")
            statusValue.Size = UDim2.new(0.3, 0, 1, 0)
            statusValue.Position = UDim2.new(0.67, 0, 0, 0)
            statusValue.BackgroundTransparency = 1
            statusValue.Text = "NORMAL"

            statusValue.TextColor3 = Color3.fromRGB(100, 255, 150)
            statusValue.TextSize = 16
            statusValue.Font = Enum.Font.GothamBold
            statusValue.TextXAlignment = Enum.TextXAlignment.Left
            statusValue.Parent = classStatusContainer
        end

        createStatusInfo()

        local function checkKillsAndUpdatePoints()
            local player = game.Players.LocalPlayer
            local currentKills = player:GetAttribute("TotalKillsFrb") or 0
            
            if currentKills > lastKillCount then
                print("Kills increased, about to save") 
                local newPoints = currentKills - lastKillCount
                availablePoints = availablePoints + newPoints
                updatePointsDisplay()
                
                updateLevel(currentKills)
                
                local pointSound = Instance.new("Sound")
                pointSound.SoundId = dokiSounds
                pointSound.TimePosition = 1.2
                pointSound.Volume = 0.5
                pointSound.Parent = guiPart

                pointSound:Play()
                
                game.Debris:AddItem(pointSound, 1)
                
                lastKillCount = currentKills
            end
        end
        
        local player = game.Players.LocalPlayer
        player:GetAttributeChangedSignal("TotalKillsFrb"):Connect(function()
            checkKillsAndUpdatePoints()
        end)

        
        lastKillCount = player:GetAttribute("TotalKillsFrb") or 0
        updateLevel(lastKillCount)

    end

    local function acceptTransition()
        TweenService:Create(Container, TweenInfo.new(0.5, Enum.EasingStyle.Back, Enum.EasingDirection.Out), {
            Size = UDim2.new(0, 650, 0, 400),
            Position = UDim2.new(0.5, -325, 0.5, -200)
        }):Play()
        
        local elementsToRemove = {
            HeaderContainer,
            MessageText,
            ButtonsContainer,
            YesButton,
            NoButton,
        }

        for _, obj in pairs(elementsToRemove) do
            if obj:IsA("TextLabel") or obj:IsA("TextButton") then
                TweenService:Create(obj, TweenInfo.new(0.3), {
                    TextTransparency = 1,
                    BackgroundTransparency = 1
                }):Play()
            elseif obj:IsA("Frame") then
                TweenService:Create(obj, TweenInfo.new(0.3), {
                    BackgroundTransparency = 1
                }):Play()
            end

            for _, child in pairs(obj:GetDescendants()) do
                if child:IsA("TextLabel") or child:IsA("TextButton") then
                    TweenService:Create(child, TweenInfo.new(0.3), {
                        TextTransparency = 1,
                        BackgroundTransparency = 1
                    }):Play()
                elseif child:IsA("Frame") then
                    TweenService:Create(child, TweenInfo.new(0.3), {
                        BackgroundTransparency = 1
                    }):Play()
                elseif child:IsA("UIStroke") then
                    TweenService:Create(child, TweenInfo.new(0.3), {
                        Transparency = 1
                    }):Play()
                end
            end
        end
        
        task.wait(0.3)
        for _, obj in pairs(elementsToRemove) do
            obj:Destroy()
        end

        createLevelingScreen()
    end



    local function kickWithEffect()
        local kickText = Instance.new("TextLabel")
        kickText.Size = UDim2.new(1, 0, 1, 0)
        kickText.Position = UDim2.new(0, 0, 0.4, 0)
        kickText.BackgroundTransparency = 1
        kickText.Text = "SYSTEM ACCESS DENIED"
        kickText.TextColor3 = Color3.fromRGB(0, 195, 255)
        kickText.TextSize = 0
        kickText.Font = Enum.Font.GothamBold
        kickText.TextStrokeTransparency = 0
        kickText.TextStrokeColor3 = Color3.fromRGB(0, 50, 100)
        kickText.Parent = MainGui

        TweenService:Create(kickText, TweenInfo.new(0.3, Enum.EasingStyle.Back, Enum.EasingDirection.Out), {
            TextSize = 50
        }):Play()

        wait(1)
        Players.LocalPlayer:Kick("System Access Denied")
    end

    YesButton.MouseButton1Click:Connect(function()
        acceptTransition()
    end)
    
    NoButton.MouseButton1Click:Connect(function()
        kickWithEffect()
    end)

    local function toggleGui()
        if not isOpen then
            guiPart.Parent = workspace
            guiPart.Transparency = 1
            
            Container.Size = UDim2.new(0, 600, 0, 0)
            Container.Position = UDim2.new(0.5, -300, 0.5, 0)
            
            TweenService:Create(guiPart, TweenInfo.new(0.3), {
                Transparency = 0.6
            }):Play()
            
            TweenService:Create(Container, TweenInfo.new(0.4, Enum.EasingStyle.Back, Enum.EasingDirection.Out), {
                Size = UDim2.new(0, 600, 0, 350),
                Position = UDim2.new(0.5, -300, 0.5, -175)
            }):Play()
            
            ambienceSound:Play()
            TweenService:Create(ambienceSound, TweenInfo.new(0.3), {
                Volume = 0.1
            }):Play()
            
            isOpen = true
        else
            TweenService:Create(guiPart, TweenInfo.new(0.3), {
                Transparency = 1
            }):Play()
            
            TweenService:Create(Container, TweenInfo.new(0.4, Enum.EasingStyle.Back, Enum.EasingDirection.In), {
                Size = UDim2.new(0, 600, 0, 0),
                Position = UDim2.new(0.5, -300, 0.5, 0)
            }):Play()
            
            TweenService:Create(ambienceSound, TweenInfo.new(0.3), {
                Volume = 0
            }):Play()
            
            task.delay(0.4, function()
                if not isOpen then
                    ambienceSound:Stop()
                    guiPart.Parent = nil
                end
            end)
            
            isOpen = false
        end
    end

    local UserInputService = game:GetService("UserInputService")
    local isMobile = UserInputService.TouchEnabled and not UserInputService.KeyboardEnabled

    local function setupInputHandling()
        if isMobile then
            local toggleButton = Instance.new("TextButton")
            toggleButton.Size = UDim2.new(0, 50, 0, 50)
            toggleButton.Position = UDim2.new(0.9, 0, 0.7, 0)
            toggleButton.BackgroundColor3 = Color3.fromRGB(0, 195, 255)
            toggleButton.BackgroundTransparency = 0.5
            toggleButton.Text = "T"
            toggleButton.TextColor3 = Color3.fromRGB(255, 255, 255)
            toggleButton.TextSize = 24
            toggleButton.Font = Enum.Font.GothamBold
            toggleButton.Parent = player.PlayerGui:WaitForChild("ScreenGui") or Instance.new("ScreenGui", player.PlayerGui)

            local glow = Instance.new("ImageLabel")
            glow.Size = UDim2.new(1.2, 0, 1.2, 0)
            glow.Position = UDim2.new(-0.1, 0, -0.1, 0)
            glow.BackgroundTransparency = 1
            glow.Image = "rbxassetid://131044285"
            glow.ImageColor3 = Color3.fromRGB(0, 195, 255)
            glow.ImageTransparency = 0.8
            glow.Parent = toggleButton

            toggleButton.MouseButton1Click:Connect(function()
                toggleGui()
            end)
        end


        UserInputService.InputBegan:Connect(function(input, gameProcessed)
            if gameProcessed then return end

            if input.KeyCode == Enum.KeyCode.T then
                toggleGui()
            end
        end)
    end

    local function setupRestingInteraction()
        if isMobile then
            local interactButton = Instance.new("TextButton")
            interactButton.Size = UDim2.new(0, 60, 0, 60)
            interactButton.Position = UDim2.new(0.8, 0, 0.6, 0)
            interactButton.BackgroundColor3 = Color3.fromRGB(0, 195, 255)
            interactButton.BackgroundTransparency = 1
            interactButton.Text = "E"
            interactButton.TextColor3 = Color3.fromRGB(0, 195, 255)
            interactButton.TextSize = 28
            interactButton.Font = Enum.Font.GothamBold
            interactButton.Visible = false
            interactButton.Parent = player.PlayerGui:WaitForChild("ScreenGui") or Instance.new("ScreenGui", player.PlayerGui)

            local glow = Instance.new("ImageLabel")
            glow.Size = UDim2.new(1.2, 0, 1.2, 0)
            glow.Position = UDim2.new(-0.1, 0, -0.1, 0)
            glow.BackgroundTransparency = 1
            glow.Image = "rbxassetid://131044285"
            glow.ImageColor3 = Color3.fromRGB(0, 195, 255)
            glow.ImageTransparency = 0.8
            glow.Parent = interactButton

            game:GetService("RunService").Heartbeat:Connect(function()
                if character and character:FindFirstChild("HumanoidRootPart") then
                    local distance = (character.HumanoidRootPart.Position - restPosition).Magnitude
                    
                    if distance <= 10 then
                        if not isInRange then
                            isInRange = true
                            interactButton.Visible = true
                            TweenService:Create(interactButton, TweenInfo.new(0.3), {BackgroundTransparency = 0.5}):Play()
                        end
                    else
                        if isInRange then
                            isInRange = false
                            if isResting then
                                handleDamage()
                            end
                            TweenService:Create(interactButton, TweenInfo.new(0.3), {BackgroundTransparency = 1}):Play()
                            wait(0.3)
                            interactButton.Visible = false
                        end
                    end
                end
            end)

            interactButton.MouseButton1Click:Connect(function()
                if isInRange then
                    isResting = true
                    storeLightingSettings()
                    applyNightSettings()
                    
                    if humanoidRootPart then
                        humanoidRootPart.Anchored = true
                    end

                    local animation = Instance.new("Animation")
                    animation.AnimationId = "rbxassetid://15503201875"
                    local animTrack = humanoid:LoadAnimation(animation)

                    local animation2 = Instance.new("Animation")
                    animation2.AnimationId = "rbxassetid://15503362953"
                    local animTrack2 = humanoid:LoadAnimation(animation2)

                    task.spawn(function()
                        animTrack:Play()
                        task.wait(1)
                        animTrack2:Play()
                    end)
                    
                    local shopGui = Instance.new("ScreenGui")
                    shopGui.Name = "MonarchMarket"
                    shopGui.Parent = player.PlayerGui
                    
                    local Container = Instance.new("Frame")
                    Container.Size = UDim2.new(0, 0, 0, 0)
                    Container.Position = UDim2.new(0.5, 0, 0.5, 0)
                    Container.BackgroundTransparency = 1
                    Container.Parent = shopGui
                    
                    local openTween = TweenService:Create(Container, TweenInfo.new(0.6, Enum.EasingStyle.Back, Enum.EasingDirection.Out), {
                        Size = UDim2.new(0, 700, 0, 500),
                        Position = UDim2.new(0.5, -350, 0.5, -250)
                    })
                    openTween:Play()

                    local dynamicBg = createDynamicBackground(Container)
                    createDynamicParticles(Container, 15)
                    createDynamicBorder(Container)

                    local Scanlines = Instance.new("Frame")
                    Scanlines.Size = UDim2.new(1, 0, 1, 0)
                    Scanlines.BackgroundTransparency = 1
                    Scanlines.ZIndex = 10
                    Scanlines.Parent = Container

                    for i = 1, 50 do
                        local line = Instance.new("Frame")
                        line.Size = UDim2.new(1, 0, 0, 1)
                        line.Position = UDim2.new(0, 0, i/50, 0)
                        line.BackgroundColor3 = Color3.fromRGB(0, 195, 255)
                        line.BackgroundTransparency = 0.95
                        line.Parent = Scanlines
                        
                        spawn(function()
                            while line.Parent do
                                local transparency = math.random(95, 98) / 100
                                local tweenInfo = TweenInfo.new(math.random(1, 2), Enum.EasingStyle.Linear)
                                local tween = TweenService:Create(line, tweenInfo, {BackgroundTransparency = transparency})
                                tween:Play()
                                wait(tweenInfo.Time)
                            end
                        end)
                    end

                    local HeaderContainer = Instance.new("Frame")
                    HeaderContainer.Size = UDim2.new(0, 200, 0, 30)
                    HeaderContainer.Position = UDim2.new(0.05, 0, 0.05, 0)
                    HeaderContainer.BackgroundTransparency = 1
                    HeaderContainer.Parent = Container
                    
                    local IconFrame = Instance.new("Frame")
                    IconFrame.Size = UDim2.new(0, 30, 0, 30)
                    IconFrame.BackgroundTransparency = 1
                    IconFrame.Parent = HeaderContainer
                    
                    local IconBorder = Instance.new("UIStroke")
                    IconBorder.Color = Color3.fromRGB(0, 195, 255)
                    IconBorder.Thickness = 1
                    IconBorder.Parent = IconFrame
                    
                    local IconText = Instance.new("TextLabel")
                    IconText.Size = UDim2.new(1, 0, 1, 0)
                    IconText.Text = "!"
                    IconText.TextColor3 = Color3.fromRGB(0, 195, 255)
                    IconText.TextSize = 20
                    IconText.Font = Enum.Font.GothamBold
                    IconText.BackgroundTransparency = 1
                    IconText.Parent = IconFrame
                    
                    local TitleFrame = Instance.new("Frame")
                    TitleFrame.Size = UDim2.new(0, 140, 0, 30)
                    TitleFrame.Position = UDim2.new(0, 40, 0, 0)
                    TitleFrame.BackgroundTransparency = 1
                    TitleFrame.Parent = HeaderContainer
                    
                    local TitleBorder = Instance.new("UIStroke")
                    TitleBorder.Color = Color3.fromRGB(0, 195, 255)
                    TitleBorder.Thickness = 1
                    TitleBorder.Parent = TitleFrame
                    
                    local TitleText = Instance.new("TextLabel")
                    TitleText.Size = UDim2.new(1, 0, 1, 0)
                    TitleText.Text = "NOTIFICATION"
                    TitleText.TextColor3 = Color3.fromRGB(0, 195, 255)
                    TitleText.TextSize = 16
                    TitleText.Font = Enum.Font.GothamBold
                    TitleText.BackgroundTransparency = 1
                    TitleText.Parent = TitleFrame
                    
                    local MessageText = Instance.new("TextLabel")
                    MessageText.Size = UDim2.new(0.9, 0, 0.2, 0)
                    MessageText.Position = UDim2.new(0.05, 0, 0.3, 0)
                    MessageText.Text = "The Monarch's Market is currently closed for maintenance.\nPlease check back later for available items."
                    MessageText.TextColor3 = Color3.fromRGB(200, 220, 255)
                    MessageText.TextSize = 22
                    MessageText.Font = Enum.Font.GothamSemibold
                    MessageText.BackgroundTransparency = 1
                    MessageText.TextStrokeTransparency = 0.7
                    MessageText.TextStrokeColor3 = Color3.fromRGB(0, 195, 255)
                    MessageText.Parent = Container

                    local TextGlow = Instance.new("ImageLabel")
                    TextGlow.Size = UDim2.new(1.2, 0, 1.2, 0)
                    TextGlow.Position = UDim2.new(-0.1, 0, -0.1, 0)
                    TextGlow.BackgroundTransparency = 1
                    TextGlow.Image = "rbxassetid://131044285"
                    TextGlow.ImageColor3 = Color3.fromRGB(0, 195, 255)
                    TextGlow.ImageTransparency = 0.8
                    TextGlow.Parent = MessageText

                    local closeButton = Instance.new("TextButton")
                    closeButton.Size = UDim2.new(0, 40, 0, 40)
                    closeButton.Position = UDim2.new(0.95, -20, 0.05, 0)
                    closeButton.BackgroundColor3 = Color3.fromRGB(255, 75, 75)
                    closeButton.BackgroundTransparency = 0.8
                    closeButton.Text = "X"
                    closeButton.TextColor3 = Color3.fromRGB(255, 255, 255)
                    closeButton.TextSize = 24
                    closeButton.Font = Enum.Font.GothamBold
                    closeButton.Parent = Container

                    closeButton.Active = false
                    closeButton.AutoButtonColor = false
                    closeButton.BackgroundColor3 = Color3.fromRGB(100, 100, 100)
                    
                    task.delay(3, function()
                        if not isResting then return end
                        closeButton.Active = true
                        closeButton.AutoButtonColor = true
                        closeButton.BackgroundColor3 = Color3.fromRGB(255, 75, 75)
                        
                        TweenService:Create(closeButton, TweenInfo.new(0.3), {
                            BackgroundTransparency = 0.8
                        }):Play()
                    end)

                    closeButton.MouseEnter:Connect(function()
                        if closeButton.Active then
                            TweenService:Create(closeButton, TweenInfo.new(0.3), {BackgroundTransparency = 0.6}):Play()
                        end
                    end)

                    closeButton.MouseLeave:Connect(function()
                        if closeButton.Active then
                            TweenService:Create(closeButton, TweenInfo.new(0.3), {BackgroundTransparency = 0.8}):Play()
                        end
                    end)

                    closeButton.MouseButton1Click:Connect(function()
                        if not closeButton.Active then return end
                        
                        isResting = false
                        restoreLightingSettings()
                        if humanoidRootPart then
                            humanoidRootPart.Anchored = false
                            animTrack2:Stop()
                        end
                        
                        local closeTween = TweenService:Create(Container, TweenInfo.new(0.4, Enum.EasingStyle.Back, Enum.EasingDirection.In), {
                            Size = UDim2.new(0, 0, 0, 0),
                            Position = UDim2.new(0.5, 0, 0.5, 0)
                        })
                        closeTween.Completed:Connect(function()
                            shopGui:Destroy()
                            animTrack:Stop()
                        end)
                        closeTween:Play()
                    end)
                end
            end)
        end

        UserInputService.InputBegan:Connect(function(input, gameProcessed)
            if not gameProcessed and isInRange and input.KeyCode == Enum.KeyCode.E then
                isResting = true
            end
        end)
    end

    setupInputHandling()
    setupRestingInteraction()

    game:GetService("UserInputService").InputBegan:Connect(function(input, gameProcessed)
        if gameProcessed then return end
        
            
        if input.KeyCode == Enum.KeyCode.K then
            availablePoints = availablePoints + getTotalSpentPoints()
            
            for stat, _ in pairs(statValues) do
                statValues[stat] = 0
            end
            
            if humanoid then
                humanoid.WalkSpeed = StatConfig.BaseWalkSpeed
            end
            
            updatePointsDisplay()
            

            local resetSound = Instance.new("Sound")
            resetSound.SoundId = dokiSounds
            resetSound.TimePosition = 1.2
            resetSound.Volume = 0.5
            resetSound.Parent = guiPart
            resetSound:Play()
            game.Debris:AddItem(resetSound, 1)
        end
    end)

end

createSoloLevelingNotification("You have acquired the qualifications\nto be a Player. Will you accept?")

local Players = game:GetService("Players")
        local player = Players.LocalPlayer
        local character = player.Character or player.CharacterAdded:Wait()
        local humanoid = character:WaitForChild("Humanoid")
        local humanoidRootPart = character:WaitForChild("HumanoidRootPart")

        local rightArm = character.HumanoidRootPart
        
        local model = game:GetObjects("rbxassetid://90712720690601")[1]

        if model then
            model.Parent = workspace
            
            if not model.PrimaryPart then
                model.PrimaryPart = model:FindFirstChild("Handle") or model:FindFirstChildWhichIsA("BasePart")
            end
            
            if model.PrimaryPart then
                
                model:PivotTo(CFrame.new(150, 439, 32))  

                
            end
        end

        local campfire = Instance.new("Sound")
        campfire.SoundId = campfireSounds
        campfire.Volume = 5
        campfire.Parent = model.PrimaryPart
        campfire.Looped = true
        campfire:Play()

local function createRestingInteraction()
    local textLabel = Instance.new("TextLabel")
    textLabel.Size = UDim2.new(0, 300, 0, 60)
    textLabel.Position = UDim2.new(0.5, -150, 0.7, 0)
    textLabel.BackgroundTransparency = 1
    textLabel.Text = "Press E to Rest"
    textLabel.TextColor3 = Color3.fromRGB(0, 195, 255)
    textLabel.TextSize = 28
    textLabel.Font = Enum.Font.GothamBold
    textLabel.TextStrokeTransparency = 0.7
    textLabel.TextStrokeColor3 = Color3.fromRGB(0, 50, 100)
    textLabel.Visible = false
    textLabel.Parent = player.PlayerGui:WaitForChild("ScreenGui") or Instance.new("ScreenGui", player.PlayerGui)

        local glow = Instance.new("ImageLabel")
    glow.Size = UDim2.new(1.2, 0, 1.2, 0)
    glow.Position = UDim2.new(-0.1, 0, -0.1, 0)
        glow.BackgroundTransparency = 1
        glow.Image = "rbxassetid://131044285"
        glow.ImageColor3 = Color3.fromRGB(0, 195, 255)
        glow.ImageTransparency = 0.8
    glow.Parent = textLabel

    local isInRange = false
    local restPosition = Vector3.new(150, 441, 32)
    local isResting = false
    local originalLighting = {}
    local fog = nil

    local function storeLightingSettings()
        local lighting = game:GetService("Lighting")
        originalLighting = {
            Brightness = lighting.Brightness,
            ClockTime = lighting.ClockTime,
            FogEnd = lighting.FogEnd,
            FogStart = lighting.FogStart,
            Ambient = lighting.Ambient
        }
    end

    local function applyNightSettings()
        local lighting = game:GetService("Lighting")
        TweenService:Create(lighting, TweenInfo.new(3), {
            Brightness = 0.2,
            ClockTime = 0,
            FogEnd = 50,
            FogStart = 10,
            Ambient = Color3.fromRGB(20, 20, 50)
        }):Play()

        fog = Instance.new("Atmosphere")
        fog.Density = 0
        fog.Color = Color3.fromRGB(0, 0, 0)    
        fog.Haze = 0
        fog.Parent = lighting
        TweenService:Create(fog, TweenInfo.new(2), {
            Density = 0.7,
            Haze = 3
        }):Play()
    end

    local function restoreLightingSettings()
        local lighting = game:GetService("Lighting")
        TweenService:Create(lighting, TweenInfo.new(1), {
            Brightness = originalLighting.Brightness,
            ClockTime = originalLighting.ClockTime,
            FogEnd = originalLighting.FogEnd,
            FogStart = originalLighting.FogStart,
            Ambient = originalLighting.Ambient
        }):Play()

        if fog then
            TweenService:Create(fog, TweenInfo.new(1), {
                Density = 0
            }):Play()
            game:GetService("Debris"):AddItem(fog, 1)
        end
    end

    local function handleDamage()
        if isResting then
            isResting = false
            restoreLightingSettings()
            if humanoidRootPart then
                humanoidRootPart.Anchored = false
            end
            if shopGui then
                shopGui:Destroy()
            end
        end
    end

    humanoid.HealthChanged:Connect(function(health)
        if health < humanoid.Health then
            handleDamage()
        end
    end)

    game:GetService("RunService").Heartbeat:Connect(function()
        if character and character:FindFirstChild("HumanoidRootPart") then
            local distance = (character.HumanoidRootPart.Position - restPosition).Magnitude
            
            if distance <= 10 then
                if not isInRange then
                    isInRange = true
                    textLabel.Visible = true
                    TweenService:Create(textLabel, TweenInfo.new(0.3), {TextTransparency = 0}):Play()
                    TweenService:Create(glow, TweenInfo.new(0.3), {ImageTransparency = 0.8}):Play()
                end
            else
                if isInRange then
                    isInRange = false
                    if isResting then
                        handleDamage()
                    end
                    TweenService:Create(textLabel, TweenInfo.new(0.3), {TextTransparency = 1}):Play()
                    TweenService:Create(glow, TweenInfo.new(0.3), {ImageTransparency = 1}):Play()
                    wait(0.3)
                    textLabel.Visible = false
                end
            end
        end
    end)

    game:GetService("UserInputService").InputBegan:Connect(function(input, gameProcessed)
        if not gameProcessed and isInRange and input.KeyCode == Enum.KeyCode.E then
            isResting = true
            storeLightingSettings()
            applyNightSettings()
            
            if humanoidRootPart then
                humanoidRootPart.Anchored = true
            end

            local animation = Instance.new("Animation")
            animation.AnimationId = "rbxassetid://15503201875"
            local animTrack = humanoid:LoadAnimation(animation)

             local animation2 = Instance.new("Animation")
            animation2.AnimationId = "rbxassetid://15503362953"
            local animTrack2 = humanoid:LoadAnimation(animation2)

            task.spawn(function()
            
            
            
            animTrack:Play()

            task.wait(1)

           

            
            animTrack2:Play()

            end)
            
            local shopGui = Instance.new("ScreenGui")
            shopGui.Name = "MonarchMarket"
            shopGui.Parent = player.PlayerGui
            
            local Container = Instance.new("Frame")
            Container.Size = UDim2.new(0, 0, 0, 0)
            Container.Position = UDim2.new(0.5, 0, 0.5, 0)
            Container.BackgroundTransparency = 1
            Container.Parent = shopGui
            
            local openTween = TweenService:Create(Container, TweenInfo.new(0.6, Enum.EasingStyle.Back, Enum.EasingDirection.Out), {
                Size = UDim2.new(0, 700, 0, 500),
                Position = UDim2.new(0.5, -350, 0.5, -250)
            })
            openTween:Play()

            local dynamicBg = createDynamicBackground(Container)
            createDynamicParticles(Container, 15)
            createDynamicBorder(Container)

            local Scanlines = Instance.new("Frame")
            Scanlines.Size = UDim2.new(1, 0, 1, 0)
            Scanlines.BackgroundTransparency = 1
            Scanlines.ZIndex = 10
            Scanlines.Parent = Container

            for i = 1, 50 do
                local line = Instance.new("Frame")
                line.Size = UDim2.new(1, 0, 0, 1)
                line.Position = UDim2.new(0, 0, i/50, 0)
                line.BackgroundColor3 = Color3.fromRGB(0, 195, 255)
                line.BackgroundTransparency = 0.95
                line.Parent = Scanlines
                
                spawn(function()
                    while line.Parent do
                        local transparency = math.random(95, 98) / 100
                        local tweenInfo = TweenInfo.new(math.random(1, 2), Enum.EasingStyle.Linear)
                        local tween = TweenService:Create(line, tweenInfo, {BackgroundTransparency = transparency})
                        tween:Play()
                        wait(tweenInfo.Time)
                    end
                end)
            end

            local HeaderContainer = Instance.new("Frame")
            HeaderContainer.Size = UDim2.new(0, 200, 0, 30)
            HeaderContainer.Position = UDim2.new(0.05, 0, 0.05, 0)
            HeaderContainer.BackgroundTransparency = 1
            HeaderContainer.Parent = Container
            
            local IconFrame = Instance.new("Frame")
            IconFrame.Size = UDim2.new(0, 30, 0, 30)
            IconFrame.BackgroundTransparency = 1
            IconFrame.Parent = HeaderContainer
            
            local IconBorder = Instance.new("UIStroke")
            IconBorder.Color = Color3.fromRGB(0, 195, 255)
            IconBorder.Thickness = 1
            IconBorder.Parent = IconFrame
            
            local IconText = Instance.new("TextLabel")
            IconText.Size = UDim2.new(1, 0, 1, 0)
            IconText.Text = "!"
            IconText.TextColor3 = Color3.fromRGB(0, 195, 255)
            IconText.TextSize = 20
            IconText.Font = Enum.Font.GothamBold
            IconText.BackgroundTransparency = 1
            IconText.Parent = IconFrame
            
            local TitleFrame = Instance.new("Frame")
            TitleFrame.Size = UDim2.new(0, 140, 0, 30)
            TitleFrame.Position = UDim2.new(0, 40, 0, 0)
            TitleFrame.BackgroundTransparency = 1
            TitleFrame.Parent = HeaderContainer
            
            local TitleBorder = Instance.new("UIStroke")
            TitleBorder.Color = Color3.fromRGB(0, 195, 255)
            TitleBorder.Thickness = 1
            TitleBorder.Parent = TitleFrame
            
            local TitleText = Instance.new("TextLabel")
            TitleText.Size = UDim2.new(1, 0, 1, 0)
            TitleText.Text = "NOTIFICATION"
            TitleText.TextColor3 = Color3.fromRGB(0, 195, 255)
            TitleText.TextSize = 16
            TitleText.Font = Enum.Font.GothamBold
            TitleText.BackgroundTransparency = 1
            TitleText.Parent = TitleFrame
            
            local MessageText = Instance.new("TextLabel")
            MessageText.Size = UDim2.new(0.9, 0, 0.2, 0)
            MessageText.Position = UDim2.new(0.05, 0, 0.3, 0)
            MessageText.Text = "The Monarch's Market is currently closed for maintenance.\nPlease check back later for available items."
            MessageText.TextColor3 = Color3.fromRGB(200, 220, 255)
            MessageText.TextSize = 22
            MessageText.Font = Enum.Font.GothamSemibold
            MessageText.BackgroundTransparency = 1
            MessageText.TextStrokeTransparency = 0.7
            MessageText.TextStrokeColor3 = Color3.fromRGB(0, 195, 255)
            MessageText.Parent = Container

            local TextGlow = Instance.new("ImageLabel")
            TextGlow.Size = UDim2.new(1.2, 0, 1.2, 0)
            TextGlow.Position = UDim2.new(-0.1, 0, -0.1, 0)
            TextGlow.BackgroundTransparency = 1
            TextGlow.Image = "rbxassetid://131044285"
            TextGlow.ImageColor3 = Color3.fromRGB(0, 195, 255)
            TextGlow.ImageTransparency = 0.8
            TextGlow.Parent = MessageText

            local closeButton = Instance.new("TextButton")
            closeButton.Size = UDim2.new(0, 40, 0, 40)
            closeButton.Position = UDim2.new(0.95, -20, 0.05, 0)
            closeButton.BackgroundColor3 = Color3.fromRGB(255, 75, 75)
            closeButton.BackgroundTransparency = 0.8
            closeButton.Text = "X"
            closeButton.TextColor3 = Color3.fromRGB(255, 255, 255)
            closeButton.TextSize = 24
            closeButton.Font = Enum.Font.GothamBold
            closeButton.Parent = Container

            closeButton.Active = false
            closeButton.AutoButtonColor = false
            closeButton.BackgroundColor3 = Color3.fromRGB(100, 100, 100)
            
            task.delay(3, function()
                if not isResting then return end
                closeButton.Active = true
                closeButton.AutoButtonColor = true
                closeButton.BackgroundColor3 = Color3.fromRGB(255, 75, 75)
                
                TweenService:Create(closeButton, TweenInfo.new(0.3), {
                    BackgroundTransparency = 0.8
                }):Play()
            end)

            closeButton.MouseEnter:Connect(function()
                if closeButton.Active then
                    TweenService:Create(closeButton, TweenInfo.new(0.3), {BackgroundTransparency = 0.6}):Play()
                end
            end)

            closeButton.MouseLeave:Connect(function()
                if closeButton.Active then
                    TweenService:Create(closeButton, TweenInfo.new(0.3), {BackgroundTransparency = 0.8}):Play()
                end
            end)

            closeButton.MouseButton1Click:Connect(function()
                if not closeButton.Active then return end
                
                isResting = false
                restoreLightingSettings()
                if humanoidRootPart then
                    humanoidRootPart.Anchored = false
                    animTrack2:Stop()
                end
                
                local closeTween = TweenService:Create(Container, TweenInfo.new(0.4, Enum.EasingStyle.Back, Enum.EasingDirection.In), {
                    Size = UDim2.new(0, 0, 0, 0),
                    Position = UDim2.new(0.5, 0, 0.5, 0)
                })
                closeTween.Completed:Connect(function()
                    shopGui:Destroy()
                    animTrack:Stop()
                end)
                closeTween:Play()
            end)
        end
    end)
end

createRestingInteraction()

local function getTotalSpentPoints()
    local total = 0
    for stat, value in pairs(statValues) do
        total = total + value
    end
    return total
end

local function handleCharacterRespawn(character)
    local humanoid = character:WaitForChild("Humanoid")
    
    for stat, value in pairs(statValues) do
        applyStat(stat, value)
    end
    
    updatePointsDisplay()
end

game.Players.LocalPlayer.CharacterAdded:Connect(handleCharacterRespawn)

if game.Players.LocalPlayer.Character then
    handleCharacterRespawn(game.Players.LocalPlayer.Character)
end
end
