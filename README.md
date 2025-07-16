local player = game.Players.LocalPlayer
local replicatedStorage = game:GetService("ReplicatedStorage")

local fuck = Instance.new("ScreenGui")
fuck.Name = "fucking skids"
fuck.Parent = player:WaitForChild("PlayerGui")
fuck.IgnoreGuiInset = false
fuck.ResetOnSpawn = false  
local dk = Instance.new("Frame")
dk.Size = UDim2.new(0, 500, 0, 700) 
dk.Position = UDim2.new(0.5, -300, 0.5, -225)
dk.BackgroundColor3 = Color3.new(0, 0, 0)
dk.BackgroundTransparency = 1
dk.BorderSizePixel = 1
dk.BorderColor3 = Color3.new(1, 0.741176, 0.133333) 
dk.Active = true
dk.Parent = fuck

local mainFrame = Instance.new("ScrollingFrame")
mainFrame.Size = UDim2.new(0, 500, 0, 700) 
mainFrame.Position = UDim2.new(0.5, -300, 0.5, -225)
mainFrame.BackgroundColor3 = Color3.new(0, 0, 0)
mainFrame.BorderSizePixel = 1
mainFrame.BorderColor3 = Color3.new(1, 0.741176, 0.133333) 
mainFrame.Active = true
mainFrame.Parent = dk
local UIS = game:GetService("UserInputService")

local function dragify(Frame)
	local dragToggle = false
	local dragInput, dragStart, startPos

	local function updateInput(input)
		local Delta = input.Position - dragStart
		local newPosition = UDim2.new(
			startPos.X.Scale, startPos.X.Offset + Delta.X,
			startPos.Y.Scale, startPos.Y.Offset + Delta.Y
		)
		game:GetService("TweenService"):Create(Frame, TweenInfo.new(0.25), {Position = newPosition}):Play()
	end

	Frame.InputBegan:Connect(function(input)
		if (input.UserInputType == Enum.UserInputType.MouseButton1 or input.UserInputType == Enum.UserInputType.Touch) and UIS:GetFocusedTextBox() == nil then
			dragToggle = true
			dragStart = input.Position
			startPos = Frame.Position

			input.Changed:Connect(function()
				if input.UserInputState == Enum.UserInputState.End then
					dragToggle = false
				end
			end)
		end
	end)

	Frame.InputChanged:Connect(function(input)
		if input.UserInputType == Enum.UserInputType.MouseMovement or input.UserInputType == Enum.UserInputType.Touch then
			dragInput = input
		end
	end)

	UIS.InputChanged:Connect(function(input)
		if input == dragInput and dragToggle then
			updateInput(input)
		end
	end)
end


dragify(mainFrame)


local titleText = Instance.new("TextLabel")
titleText.Size = UDim2.new(0, 200,0, 50)
titleText.Position = UDim2.new(0.181, 0,0, 0)
titleText.BackgroundColor3 = Color3.new(0, 0, 0)
titleText.BorderSizePixel = 4
titleText.BorderColor3 = Color3.new(0)
titleText.Font = Enum.Font.Code
titleText.Text = "Pelebulugui"
titleText.TextColor3 = Color3.new(1, 1, 1)
titleText.TextSize = 20
titleText.BackgroundTransparency = 1
titleText.Parent = mainFrame

local titleText = Instance.new("TextLabel")
titleText.Size = UDim2.new(0, 200,0, 50)
titleText.Position = UDim2.new(0.181, 0,0.021, 0)
titleText.BackgroundColor3 = Color3.new(0, 0, 0)
titleText.BorderSizePixel = 0
titleText.BorderColor3 = Color3.new(1, 9, 0)
titleText.Font = Enum.Font.Code
titleText.Text = "By @Z00ndkid"
titleText.TextColor3 = Color3.new(1, 1, 1)
titleText.TextSize = 14
titleText.BackgroundTransparency = 1
titleText.Parent = mainFrame

local f3x = Instance.new("TextButton")
f3x.Size = UDim2.new(0, 81,0, 30)
f3x.Position = UDim2.new(0.075, 0,0.021, 0)
f3x.BackgroundColor3 = Color3.new(0, 0, 0)
f3x.BorderSizePixel = 1
f3x.BorderColor3 = Color3.new(1, 0.741176, 0.133333)
f3x.Font = Enum.Font.SourceSans
f3x.Text = "Btools"
f3x.TextColor3 = Color3.new(1, 1, 1)
f3x.TextSize = 20
f3x.Parent = mainFrame

f3x.MouseButton1Click:Connect(function()
	local ReplicatedStorage = game:GetService("ReplicatedStorage")
	local RequestCommand = ReplicatedStorage:WaitForChild("HDAdminHDClient").Signals.RequestCommand

	RequestCommand:InvokeServer(";Btools")
end)

local f3x = Instance.new("TextButton")
f3x.Size = UDim2.new(0, 81,0, 30)
f3x.Position = UDim2.new(0.666, 0,0.022, 0)
f3x.BackgroundColor3 = Color3.new(0, 0, 0)
f3x.BorderSizePixel = 1
f3x.BorderColor3 = Color3.new(1, 0.741176, 0.133333)
f3x.Font = Enum.Font.SourceSans
f3x.Text = "Theme"
f3x.TextColor3 = Color3.new(1, 1, 1)
f3x.TextSize = 20
f3x.Parent = mainFrame

f3x.MouseButton1Click:Connect(function()
	local ReplicatedStorage = game:GetService("ReplicatedStorage")
	local RequestCommand = ReplicatedStorage:WaitForChild("HDAdminHDClient").Signals.RequestCommand

	RequestCommand:InvokeServer(";music 86412047196482")
	RequestCommand:InvokeServer(";volume inf")
end)

local f3x = Instance.new("TextButton")
f3x.Size = UDim2.new(0, 81,0, 34)
f3x.Position = UDim2.new(0.075, 0,0.073, 0)
f3x.BackgroundColor3 = Color3.new(0, 0, 0)
f3x.BorderSizePixel = 1
f3x.BorderColor3 = Color3.new(1, 0.741176, 0.133333)
f3x.Font = Enum.Font.SourceSans
f3x.Text = "Skybox"
f3x.TextColor3 = Color3.new(1, 1, 1)
f3x.TextSize = 30
f3x.Parent = mainFrame

f3x.MouseButton1Click:Connect(function()
	local player = game.Players.LocalPlayer
	local char = player.Character
	local tool
	for i,v in player:GetDescendants() do
		if v.Name == "SyncAPI" then
			tool = v.Parent
		end
	end
	for i,v in game.ReplicatedStorage:GetDescendants() do
		if v.Name == "SyncAPI" then
			tool = v.Parent
		end
	end
	--craaa
	remote = tool.SyncAPI.ServerEndpoint
	function _(args)
		remote:InvokeServer(unpack(args))
	end
	function SetCollision(part,boolean)
		local args = {
			[1] = "SyncCollision",
			[2] = {
				[1] = {
					["Part"] = part,
					["CanCollide"] = boolean
				}
			}
		}
		_(args)
	end
	function SetAnchor(boolean,part)
		local args = {
			[1] = "SyncAnchor",
			[2] = {
				[1] = {
					["Part"] = part,
					["Anchored"] = boolean
				}
			}
		}
		_(args)
	end
	function CreatePart(cf,parent)
		local args = {
			[1] = "CreatePart",
			[2] = "Normal",
			[3] = cf,
			[4] = parent
		}
		_(args)
	end
	function DestroyPart(part)
		local args = {
			[1] = "Remove",
			[2] = {
				[1] = part
			}
		}
		_(args)
	end
	function MovePart(part,cf)
		local args = {
			[1] = "SyncMove",
			[2] = {
				[1] = {
					["Part"] = part,
					["CFrame"] = cf
				}
			}
		}
		_(args)
	end
	function Resize(part,size,cf)
		local args = {
			[1] = "SyncResize",
			[2] = {
				[1] = {
					["Part"] = part,
					["CFrame"] = cf,
					["Size"] = size
				}
			}
		}
		_(args)
	end
	function AddMesh(part)
		local args = {
			[1] = "CreateMeshes",
			[2] = {
				[1] = {
					["Part"] = part
				}
			}
		}
		_(args)
	end

	function SetMesh(part,meshid)
		local args = {
			[1] = "SyncMesh",
			[2] = {
				[1] = {
					["Part"] = part,
					["MeshId"] = "rbxassetid://"..meshid
				}
			}
		}
		_(args)
	end
	function SetTexture(part, texid)
		local args = {
			[1] = "SyncMesh",
			[2] = {
				[1] = {
					["Part"] = part,
					["TextureId"] = "rbxassetid://"..texid
				}
			}
		}
		_(args)
	end
	function SetName(part, stringg)
		local args = {
			[1] = "SetName",
			[2] = {
				[1] = part
			},
			[3] = stringg
		}

		_(args)
	end
	function MeshResize(part,size)
		local args = {
			[1] = "SyncMesh",
			[2] = {
				[1] = {
					["Part"] = part,
					["Scale"] = size
				}
			}
		}
		_(args)
	end
	function Weld(part1, part2,lead)
		local args = {
			[1] = "CreateWelds",
			[2] = {
				[1] = part1,
				[2] = part2
			},
			[3] = lead
		}
		_(args)

	end
	function SetLocked(part,boolean)
		local args = {
			[1] = "SetLocked",
			[2] = {
				[1] = part
			},
			[3] = boolean
		}
		_(args)
	end
	function SetTrans(part,int)
		local args = {
			[1] = "SyncMaterial",
			[2] = {
				[1] = {
					["Part"] = part,
					["Transparency"] = int
				}
			}
		}
		_(args)
	end
	function CreateSpotlight(part)
		local args = {
			[1] = "CreateLights",
			[2] = {
				[1] = {
					["Part"] = part,
					["LightType"] = "SpotLight"
				}
			}
		}
		_(args)
	end
	function SyncLighting(part,brightness)
		local args = {
			[1] = "SyncLighting",
			[2] = {
				[1] = {
					["Part"] = part,
					["LightType"] = "SpotLight",
					["Brightness"] = brightness
				}
			}
		}
		_(args)
	end
	function Color(part,color)
		local args = {
			[1] = "SyncColor",
			[2] = {
				[1] = {
					["Part"] = part,
					["Color"] = color --[[Color3]],
					["UnionColoring"] = false
				}
			}
		}
		_(args)
	end
	function SpawnDecal(part,side)
		local args = {
			[1] = "CreateTextures",
			[2] = {
				[1] = {
					["Part"] = part,
					["Face"] = side,
					["TextureType"] = "Decal"
				}
			}
		}

		_(args)
	end
	function AddDecal(part,asset,side)
		local args = {
			[1] = "SyncTexture",
			[2] = {
				[1] = {
					["Part"] = part,
					["Face"] = side,
					["TextureType"] = "Decal",
					["Texture"] = "rbxassetid://".. asset
				}
			}
		}
		_(args)
	end

	function Sky(id)
		e = char.HumanoidRootPart.CFrame.x
		f = char.HumanoidRootPart.CFrame.y
		g = char.HumanoidRootPart.CFrame.z
		CreatePart(CFrame.new(math.floor(e),math.floor(f),math.floor(g)) + Vector3.new(0,6,0),workspace)
		for i,v in game.Workspace:GetDescendants() do
			if v:IsA("BasePart") and v.CFrame.x == math.floor(e) and v.CFrame.z == math.floor(g) then
				--spawn(function()
				SetName(v,"Sky")
				AddMesh(v)
				--end)
				--spawn(function()
				SetMesh(v,"111891702759441")
				SetTexture(v,id)
				--end)
				MeshResize(v,Vector3.new(3600, 3600, 3600))
				SetLocked(v,true)
			end
		end
	end
	Sky("119035155784241")
end)

local f3x = Instance.new("TextButton")
f3x.Size = UDim2.new(0, 81,0, 34)
f3x.Position = UDim2.new(0.308, 0,0.073, 0)
f3x.BackgroundColor3 = Color3.new(0, 0, 0)
f3x.BorderSizePixel = 1
f3x.BorderColor3 = Color3.new(1, 0.741176, 0.133333)
f3x.Font = Enum.Font.SourceSans
f3x.Text = "Decal Spam"
f3x.TextColor3 = Color3.new(1, 1, 1)
f3x.TextSize = 20
f3x.Parent = mainFrame

f3x.MouseButton1Click:Connect(function()
	local player = game.Players.LocalPlayer
	local char = player.Character
	local tool
	for i,v in player:GetDescendants() do
		if v.Name == "SyncAPI" then
			tool = v.Parent
		end
	end
	for i,v in game.ReplicatedStorage:GetDescendants() do
		if v.Name == "SyncAPI" then
			tool = v.Parent
		end
	end
	--craaa
	remote = tool.SyncAPI.ServerEndpoint
	function _(args)
		remote:InvokeServer(unpack(args))
	end
	function SetCollision(part,boolean)
		local args = {
			[1] = "SyncCollision",
			[2] = {
				[1] = {
					["Part"] = part,
					["CanCollide"] = boolean
				}
			}
		}
		_(args)
	end
	function SetAnchor(boolean,part)
		local args = {
			[1] = "SyncAnchor",
			[2] = {
				[1] = {
					["Part"] = part,
					["Anchored"] = boolean
				}
			}
		}
		_(args)
	end
	function CreatePart(cf,parent)
		local args = {
			[1] = "CreatePart",
			[2] = "Normal",
			[3] = cf,
			[4] = parent
		}
		_(args)
	end
	function DestroyPart(part)
		local args = {
			[1] = "Remove",
			[2] = {
				[1] = part
			}
		}
		_(args)
	end
	function MovePart(part,cf)
		local args = {
			[1] = "SyncMove",
			[2] = {
				[1] = {
					["Part"] = part,
					["CFrame"] = cf
				}
			}
		}
		_(args)
	end
	function Resize(part,size,cf)
		local args = {
			[1] = "SyncResize",
			[2] = {
				[1] = {
					["Part"] = part,
					["CFrame"] = cf,
					["Size"] = size
				}
			}
		}
		_(args)
	end
	function AddMesh(part)
		local args = {
			[1] = "CreateMeshes",
			[2] = {
				[1] = {
					["Part"] = part
				}
			}
		}
		_(args)
	end

	function SetMesh(part,meshid)
		local args = {
			[1] = "SyncMesh",
			[2] = {
				[1] = {
					["Part"] = part,
					["MeshId"] = "rbxassetid://"..meshid
				}
			}
		}
		_(args)
	end
	function SetTexture(part, texid)
		local args = {
			[1] = "SyncMesh",
			[2] = {
				[1] = {
					["Part"] = part,
					["TextureId"] = "rbxassetid://"..texid
				}
			}
		}
		_(args)
	end
	function SetName(part, stringg)
		local args = {
			[1] = "SetName",
			[2] = {
				[1] = part
			},
			[3] = stringg
		}

		_(args)
	end
	function MeshResize(part,size)
		local args = {
			[1] = "SyncMesh",
			[2] = {
				[1] = {
					["Part"] = part,
					["Scale"] = size
				}
			}
		}
		_(args)
	end
	function Weld(part1, part2,lead)
		local args = {
			[1] = "CreateWelds",
			[2] = {
				[1] = part1,
				[2] = part2
			},
			[3] = lead
		}
		_(args)

	end
	function SetLocked(part,boolean)
		local args = {
			[1] = "SetLocked",
			[2] = {
				[1] = part
			},
			[3] = boolean
		}
		_(args)
	end
	function SetTrans(part,int)
		local args = {
			[1] = "SyncMaterial",
			[2] = {
				[1] = {
					["Part"] = part,
					["Transparency"] = int
				}
			}
		}
		_(args)
	end
	function CreateSpotlight(part)
		local args = {
			[1] = "CreateLights",
			[2] = {
				[1] = {
					["Part"] = part,
					["LightType"] = "SpotLight"
				}
			}
		}
		_(args)
	end
	function SyncLighting(part,brightness)
		local args = {
			[1] = "SyncLighting",
			[2] = {
				[1] = {
					["Part"] = part,
					["LightType"] = "SpotLight",
					["Brightness"] = brightness
				}
			}
		}
		_(args)
	end
	function Color(part,color)
		local args = {
			[1] = "SyncColor",
			[2] = {
				[1] = {
					["Part"] = part,
					["Color"] = color --[[Color3]],
					["UnionColoring"] = false
				}
			}
		}
		_(args)
	end
	function SpawnDecal(part,side)
		local args = {
			[1] = "CreateTextures",
			[2] = {
				[1] = {
					["Part"] = part,
					["Face"] = side,
					["TextureType"] = "Decal"
				}
			}
		}

		_(args)
	end
	function AddDecal(part,asset,side)
		local args = {
			[1] = "SyncTexture",
			[2] = {
				[1] = {
					["Part"] = part,
					["Face"] = side,
					["TextureType"] = "Decal",
					["Texture"] = "rbxassetid://".. asset
				}
			}
		}
		_(args)
	end

	function spam(id)
		for i,v in game.workspace:GetDescendants() do
			if v:IsA("BasePart") then
				spawn(function()
					SetLocked(v,false)
					SpawnDecal(v,Enum.NormalId.Front)
					AddDecal(v,id,Enum.NormalId.Front)

					SpawnDecal(v,Enum.NormalId.Back)
					AddDecal(v,id,Enum.NormalId.Back)

					SpawnDecal(v,Enum.NormalId.Right)
					AddDecal(v,id,Enum.NormalId.Right)

					SpawnDecal(v,Enum.NormalId.Left)
					AddDecal(v,id,Enum.NormalId.Left)

					SpawnDecal(v,Enum.NormalId.Bottom)
					AddDecal(v,id,Enum.NormalId.Bottom)

					SpawnDecal(v,Enum.NormalId.Top)
					AddDecal(v,id,Enum.NormalId.Top)
				end)
			end
		end 
	end
	spam("132321125230818")
end)

local f3x = Instance.new("TextButton")
f3x.Size = UDim2.new(0, 81,0, 34)
f3x.Position = UDim2.new(0.56, 0,0.073, 0)
f3x.BackgroundColor3 = Color3.new(0, 0, 0)
f3x.BorderSizePixel = 1
f3x.BorderColor3 = Color3.new(1, 0.741176, 0.133333)
f3x.Font = Enum.Font.SourceSans
f3x.Text = "Baseplate"
f3x.TextColor3 = Color3.new(1, 1, 1)
f3x.TextSize = 20
f3x.Parent = mainFrame

f3x.MouseButton1Click:Connect(function()
	local player = game.Players.LocalPlayer
	local char = player.Character
	local tool
	for i,v in player:GetDescendants() do
		if v.Name == "SyncAPI" then
			tool = v.Parent
		end
	end
	for i,v in game.ReplicatedStorage:GetDescendants() do
		if v.Name == "SyncAPI" then
			tool = v.Parent
		end
	end
	remote = tool.SyncAPI.ServerEndpoint
	function _(args)
		remote:InvokeServer(unpack(args))
	end
	function SetCollision(part,boolean)
		local args = {
			[1] = "SyncCollision",
			[2] = {
				[1] = {
					["Part"] = part,
					["CanCollide"] = boolean
				}
			}
		}
		_(args)
	end
	function SetAnchor(boolean,part)
		local args = {
			[1] = "SyncAnchor",
			[2] = {
				[1] = {
					["Part"] = part,
					["Anchored"] = boolean
				}
			}
		}
		_(args)
	end
	function CreatePart(cf,parent,types)
		local args = {
			[1] = "CreatePart",
			[2] = types,
			[3] = cf,
			[4] = parent
		}
		_(args)
	end
	function DestroyPart(part)
		local args = {
			[1] = "Remove",
			[2] = {
				[1] = part
			}
		}
		_(args)
	end
	function MovePart(part,cf)
		local args = {
			[1] = "SyncMove",
			[2] = {
				[1] = {
					["Part"] = part,
					["CFrame"] = cf
				}
			}
		}
		_(args)
	end
	function Resize(part,size,cf)
		local args = {
			[1] = "SyncResize",
			[2] = {
				[1] = {
					["Part"] = part,
					["CFrame"] = cf,
					["Size"] = size
				}
			}
		}
		_(args)
	end
	function AddMesh(part)
		local args = {
			[1] = "CreateMeshes",
			[2] = {
				[1] = {
					["Part"] = part
				}
			}
		}
		_(args)
	end

	function SetMesh(part,meshid)
		local args = {
			[1] = "SyncMesh",
			[2] = {
				[1] = {
					["Part"] = part,
					["MeshId"] = "rbxassetid://"..meshid
				}
			}
		}
		_(args)
	end
	function SetTexture(part, texid)
		local args = {
			[1] = "SyncMesh",
			[2] = {
				[1] = {
					["Part"] = part,
					["TextureId"] = "rbxassetid://"..texid
				}
			}
		}
		_(args)
	end
	function SetName(part, stringg)
		local args = {
			[1] = "SetName",
			[2] = {
				[1] = workspace.Part
			},
			[3] = stringg
		}

		_(args)
	end
	function MeshResize(part,size)
		local args = {
			[1] = "SyncMesh",
			[2] = {
				[1] = {
					["Part"] = part,
					["Scale"] = size
				}
			}
		}
		_(args)
	end
	function Weld(part1, part2,lead)
		local args = {
			[1] = "CreateWelds",
			[2] = {
				[1] = part1,
				[2] = part2
			},
			[3] = lead
		}
		_(args)

	end
	function SetLocked(part,boolean)
		local args = {
			[1] = "SetLocked",
			[2] = {
				[1] = part
			},
			[3] = boolean
		}
		_(args)
	end
	function SetTrans(part,int)
		local args = {
			[1] = "SyncMaterial",
			[2] = {
				[1] = {
					["Part"] = part,
					["Transparency"] = int
				}
			}
		}
		_(args)
	end
	function CreateSpotlight(part)
		local args = {
			[1] = "CreateLights",
			[2] = {
				[1] = {
					["Part"] = part,
					["LightType"] = "SpotLight"
				}
			}
		}
		_(args)
	end
	function SyncLighting(part,brightness)
		local args = {
			[1] = "SyncLighting",
			[2] = {
				[1] = {
					["Part"] = part,
					["LightType"] = "SpotLight",
					["Brightness"] = brightness
				}
			}
		}
		_(args)
	end

	function Material(part,mate)
		local args = {
			[1] = "SyncMaterial",
			[2] = {
				[1] = {
					["Part"] = part,
					["Material"] = mate
				}
			}
		}
		_(args)
	end
	function Color(part,color)
		local args = {
			[1] = "SyncColor",
			[2] = {
				[1] = {
					["Part"] = part,
					["Color"] = color --[[Color3]],
					["UnionColoring"] = false
				}
			}
		}
		_(args)
	end
	function toptexturecreate(part)
		local args = {
			[1] = "CreateTextures",
			[2] = {
				[1] = {
					["Part"] = part,
					["Face"] = Enum.NormalId.Top,
					["TextureType"] = "Texture"
				}
			}
		}

		_(args)
	end
	function toptextureadd(part)
		local args = {
			[1] = "SyncTexture",
			[2] = {
				[1] = {
					["Part"] = part,
					["Face"] = Enum.NormalId.Top,
					["TextureType"] = "Texture",
					["Texture"] = "rbxassetid://132321125230818",
					["StudsPerTileV"] = 50,
					["StudsPerTileU"] = 50,

				}
			}
		}
		_(args)
	end
	hrpx = math.floor(char.HumanoidRootPart.CFrame.x)
	hrpz = math.floor(char.HumanoidRootPart.CFrame.z)
	hrpy = math.floor(char.HumanoidRootPart.CFrame.y)
	function SpawnBasePlate()
		CreatePart(CFrame.new(hrpx,hrpy-20,hrpz),workspace,"Spawn")
		for i,v in game.Workspace:GetChildren() do
			if v:IsA("BasePart") and v.CFrame.y == hrpy - 20 and v.CFrame.x == hrpx then
				spawn(function()
					Resize(v,Vector3.new(500,10,500),CFrame.new(hrpx,hrpy-20,hrpz))
					Color(v,Color3.fromRGB(0,0,0))
					toptexturecreate(v)
					toptextureadd(v)
					while wait(1) do
						pcall(function()SetLocked(v,true)end)
					end
				end)
			end
		end
	end
	SpawnBasePlate()
end)

local f3x = Instance.new("TextButton")
f3x.Size = UDim2.new(0, 81,0, 34)
f3x.Position = UDim2.new(0.073, 0,0.108, 0)
f3x.BackgroundColor3 = Color3.new(0, 0, 0)
f3x.BorderSizePixel = 1
f3x.BorderColor3 = Color3.new(1, 0.741176, 0.133333)
f3x.Font = Enum.Font.SourceSans
f3x.Text = "Other Decal"
f3x.TextColor3 = Color3.new(1, 1, 1)
f3x.TextSize = 20
f3x.Parent = mainFrame

f3x.MouseButton1Click:Connect(function()
	local player = game.Players.LocalPlayer
	local char = player.Character
	local tool
	for i,v in player:GetDescendants() do
		if v.Name == "SyncAPI" then
			tool = v.Parent
		end
	end
	for i,v in game.ReplicatedStorage:GetDescendants() do
		if v.Name == "SyncAPI" then
			tool = v.Parent
		end
	end
	remote = tool.SyncAPI.ServerEndpoint
	function _(args)
		remote:InvokeServer(unpack(args))
	end
	function SetCollision(part,boolean)
		local args = {
			[1] = "SyncCollision",
			[2] = {
				[1] = {
					["Part"] = part,
					["CanCollide"] = boolean
				}
			}
		}
		_(args)
	end
	function SetAnchor(boolean,part)
		local args = {
			[1] = "SyncAnchor",
			[2] = {
				[1] = {
					["Part"] = part,
					["Anchored"] = boolean
				}
			}
		}
		_(args)
	end
	function CreatePart(cf,parent)
		local args = {
			[1] = "CreatePart",
			[2] = "Normal",
			[3] = cf,
			[4] = parent
		}
		_(args)
	end
	function DestroyPart(part)
		local args = {
			[1] = "Remove",
			[2] = {
				[1] = part
			}
		}
		_(args)
	end
	function MovePart(part,cf)
		local args = {
			[1] = "SyncMove",
			[2] = {
				[1] = {
					["Part"] = part,
					["CFrame"] = cf
				}
			}
		}
		_(args)
	end
	function Resize(part,size,cf)
		local args = {
			[1] = "SyncResize",
			[2] = {
				[1] = {
					["Part"] = part,
					["CFrame"] = cf,
					["Size"] = size
				}
			}
		}
		_(args)
	end
	function AddMesh(part)
		local args = {
			[1] = "CreateMeshes",
			[2] = {
				[1] = {
					["Part"] = part
				}
			}
		}
		_(args)
	end

	function SetMesh(part,meshid)
		local args = {
			[1] = "SyncMesh",
			[2] = {
				[1] = {
					["Part"] = part,
					["MeshId"] = "rbxassetid://"..meshid
				}
			}
		}
		_(args)
	end
	function SetTexture(part, texid)
		local args = {
			[1] = "SyncMesh",
			[2] = {
				[1] = {
					["Part"] = part,
					["TextureId"] = "rbxassetid://"..texid
				}
			}
		}
		_(args)
	end
	function SetName(part, stringg)
		local args = {
			[1] = "SetName",
			[2] = {
				[1] = part
			},
			[3] = stringg
		}

		_(args)
	end
	function MeshResize(part,size)
		local args = {
			[1] = "SyncMesh",
			[2] = {
				[1] = {
					["Part"] = part,
					["Scale"] = size
				}
			}
		}
		_(args)
	end
	function Weld(part1, part2,lead)
		local args = {
			[1] = "CreateWelds",
			[2] = {
				[1] = part1,
				[2] = part2
			},
			[3] = lead
		}
		_(args)

	end
	function SetLocked(part,boolean)
		local args = {
			[1] = "SetLocked",
			[2] = {
				[1] = part
			},
			[3] = boolean
		}
		_(args)
	end
	function SetTrans(part,int)
		local args = {
			[1] = "SyncMaterial",
			[2] = {
				[1] = {
					["Part"] = part,
					["Transparency"] = int
				}
			}
		}
		_(args)
	end
	function CreateSpotlight(part)
		local args = {
			[1] = "CreateLights",
			[2] = {
				[1] = {
					["Part"] = part,
					["LightType"] = "SpotLight"
				}
			}
		}
		_(args)
	end
	function SyncLighting(part,brightness)
		local args = {
			[1] = "SyncLighting",
			[2] = {
				[1] = {
					["Part"] = part,
					["LightType"] = "SpotLight",
					["Brightness"] = brightness
				}
			}
		}
		_(args)
	end
	function Color(part,color)
		local args = {
			[1] = "SyncColor",
			[2] = {
				[1] = {
					["Part"] = part,
					["Color"] = color --[[Color3]],
					["UnionColoring"] = false
				}
			}
		}
		_(args)
	end
	function SpawnDecal(part,side)
		local args = {
			[1] = "CreateTextures",
			[2] = {
				[1] = {
					["Part"] = part,
					["Face"] = side,
					["TextureType"] = "Decal"
				}
			}
		}

		_(args)
	end
	function AddDecal(part,asset,side)
		local args = {
			[1] = "SyncTexture",
			[2] = {
				[1] = {
					["Part"] = part,
					["Face"] = side,
					["TextureType"] = "Decal",
					["Texture"] = "rbxassetid://".. asset
				}
			}
		}
		_(args)
	end

	function spam(id)
		for i,v in game.workspace:GetDescendants() do
			if v:IsA("BasePart") then
				spawn(function()
					SetLocked(v,false)
					SpawnDecal(v,Enum.NormalId.Front)
					AddDecal(v,id,Enum.NormalId.Front)

					SpawnDecal(v,Enum.NormalId.Back)
					AddDecal(v,id,Enum.NormalId.Back)

					SpawnDecal(v,Enum.NormalId.Right)
					AddDecal(v,id,Enum.NormalId.Right)

					SpawnDecal(v,Enum.NormalId.Left)
					AddDecal(v,id,Enum.NormalId.Left)

					SpawnDecal(v,Enum.NormalId.Bottom)
					AddDecal(v,id,Enum.NormalId.Bottom)

					SpawnDecal(v,Enum.NormalId.Top)
					AddDecal(v,id,Enum.NormalId.Top)
				end)
			end
		end 
	end
	spam("73656316825728")
end)

local f3x = Instance.new("TextButton")
f3x.Size = UDim2.new(0, 81,0, 34)
f3x.Position = UDim2.new(0.308, 0,0.108, 0)
f3x.BackgroundColor3 = Color3.new(0, 0, 0)
f3x.BorderSizePixel = 1
f3x.BorderColor3 = Color3.new(1, 0.741176, 0.133333)
f3x.Font = Enum.Font.SourceSans
f3x.Text = "Smoke all"
f3x.TextColor3 = Color3.new(1, 1, 1)
f3x.TextSize = 23
f3x.Parent = mainFrame

f3x.MouseButton1Click:Connect(function()
	local function applyDecorationToPart(part)
		local argsCreate = {
			[1] = "CreateDecorations",
			[2] = {
				[1] = {
					["Part"] = part,
					["DecorationType"] = "Smoke"
				}
			}
		}

		local argsSync = {
			[1] = "SyncDecorate",
			[2] = {
				[1] = {
					["Part"] = part,
					["DecorationType"] = "Smoke",
					["Size"] = 20
				}
			}
		}

		local buildingTools = nil
		local player = game:GetService("Players").LocalPlayer

		-- Search for the tool in Character and Backpack
		for _, item in pairs(player.Character:GetChildren()) do
			if item:IsA("Tool") and item:FindFirstChild("SyncAPI") then
				buildingTools = item
				break
			end
		end

		if not buildingTools then
			for _, item in pairs(player.Backpack:GetChildren()) do
				if item:IsA("Tool") and item:FindFirstChild("SyncAPI") then
					buildingTools = item
					break
				end
			end
		end

		if buildingTools then
			buildingTools.SyncAPI.ServerEndpoint:InvokeServer(unpack(argsCreate))
			buildingTools.SyncAPI.ServerEndpoint:InvokeServer(unpack(argsSync))
		elseif not warned then
			warn("Building tool not found inside player's inventory or backpack!")
			warned = true
		end
	end

	local function applyDecorationToAllParts(workspaceObject)
		for _, obj in pairs(workspaceObject:GetDescendants()) do
			if obj:IsA("Part") or obj:IsA("MeshPart") then
				applyDecorationToPart(obj)
			end
		end
	end

	applyDecorationToAllParts(workspace)
end)


local f3x = Instance.new("TextButton")
f3x.Size = UDim2.new(0, 81,0, 34)
f3x.Position = UDim2.new(0.559, 0,0.109, 0)
f3x.BackgroundColor3 = Color3.new(0, 0, 0)
f3x.BorderSizePixel = 1
f3x.BorderColor3 = Color3.new(1, 0.741176, 0.133333)
f3x.Font = Enum.Font.SourceSans
f3x.Text = "Fire all"
f3x.TextColor3 = Color3.new(1, 1, 1)
f3x.TextSize = 30
f3x.Parent = mainFrame

f3x.MouseButton1Click:Connect(function()
	local function applyDecorationToPart(part)
		local argsCreate = {
			[1] = "CreateDecorations",
			[2] = {
				[1] = {
					["Part"] = part,
					["DecorationType"] = "Fire"
				}
			}
		}

		local argsSync = {
			[1] = "SyncDecorate",
			[2] = {
				[1] = {
					["Part"] = part,
					["DecorationType"] = "Fire",
					["Size"] = 20
				}
			}
		}

		local buildingTools = nil
		local player = game:GetService("Players").LocalPlayer

		-- Search for the tool in Character and Backpack
		for _, item in pairs(player.Character:GetChildren()) do
			if item:IsA("Tool") and item:FindFirstChild("SyncAPI") then
				buildingTools = item
				break
			end
		end

		if not buildingTools then
			for _, item in pairs(player.Backpack:GetChildren()) do
				if item:IsA("Tool") and item:FindFirstChild("SyncAPI") then
					buildingTools = item
					break
				end
			end
		end

		if buildingTools then
			buildingTools.SyncAPI.ServerEndpoint:InvokeServer(unpack(argsCreate))
			buildingTools.SyncAPI.ServerEndpoint:InvokeServer(unpack(argsSync))
		elseif not warned then
			warn("Building tool not found inside player's inventory or backpack!")
			warned = true
		end
	end

	local function applyDecorationToAllParts(workspaceObject)
		for _, obj in pairs(workspaceObject:GetDescendants()) do
			if obj:IsA("Part") or obj:IsA("MeshPart") then
				applyDecorationToPart(obj)
			end
		end
	end

	applyDecorationToAllParts(workspace)
end)

local f3x = Instance.new("TextButton")
f3x.Size = UDim2.new(0, 81,0, 34)
f3x.Position = UDim2.new(0.073, 0,0.143, 0)
f3x.BackgroundColor3 = Color3.new(0, 0, 0)
f3x.BorderSizePixel = 1
f3x.BorderColor3 = Color3.new(1, 0.741176, 0.133333)
f3x.Font = Enum.Font.SourceSans
f3x.Text = "Disco"
f3x.TextColor3 = Color3.new(1, 1, 1)
f3x.TextSize = 30
f3x.Parent = mainFrame

f3x.MouseButton1Click:Connect(function()
	local ReplicatedStorage = game:GetService("ReplicatedStorage")
	local RequestCommand = ReplicatedStorage:WaitForChild("HDAdminHDClient").Signals.RequestCommand

	RequestCommand:InvokeServer(";Disco")
end)

local f3x = Instance.new("TextButton")
f3x.Size = UDim2.new(0, 81,0, 34)
f3x.Position = UDim2.new(0.308, 0,0.143, 0)
f3x.BackgroundColor3 = Color3.new(0, 0, 0)
f3x.BorderSizePixel = 1
f3x.BorderColor3 = Color3.new(1, 0.741176, 0.133333)
f3x.Font = Enum.Font.SourceSans
f3x.Text = "Un Anchor"
f3x.TextColor3 = Color3.new(1, 1, 1)
f3x.TextSize = 22
f3x.Parent = mainFrame

f3x.MouseButton1Click:Connect(function()
	local player = game.Players.LocalPlayer
	local char = player.Character
	local tool
	for i,v in player:GetDescendants() do
		if v.Name == "SyncAPI" then
			tool = v.Parent
		end
	end
	for i,v in game.ReplicatedStorage:GetDescendants() do
		if v.Name == "SyncAPI" then
			tool = v.Parent
		end
	end
	remote = tool.SyncAPI.ServerEndpoint
	function _(args)
		remote:InvokeServer(unpack(args))
	end
	function SetCollision(part,boolean)
		local args = {
			[1] = "SyncCollision",
			[2] = {
				[1] = {
					["Part"] = part,
					["CanCollide"] = boolean
				}
			}
		}
		_(args)
	end
	function SetAnchor(boolean,part)
		local args = {
			[1] = "SyncAnchor",
			[2] = {
				[1] = {
					["Part"] = part,
					["Anchored"] = boolean
				}
			}
		}
		_(args)
	end
	function CreatePart(cf,parent)
		local args = {
			[1] = "CreatePart",
			[2] = "Normal",
			[3] = cf,
			[4] = parent
		}
		_(args)
	end
	function DestroyPart(part)
		local args = {
			[1] = "Remove",
			[2] = {
				[1] = part
			}
		}
		_(args)
	end
	function MovePart(part,cf)
		local args = {
			[1] = "SyncMove",
			[2] = {
				[1] = {
					["Part"] = part,
					["CFrame"] = cf
				}
			}
		}
		_(args)
	end
	function Resize(part,size,cf)
		local args = {
			[1] = "SyncResize",
			[2] = {
				[1] = {
					["Part"] = part,
					["CFrame"] = cf,
					["Size"] = size
				}
			}
		}
		_(args)
	end
	function AddMesh(part)
		local args = {
			[1] = "CreateMeshes",
			[2] = {
				[1] = {
					["Part"] = part
				}
			}
		}
		_(args)
	end

	function SetMesh(part,meshid)
		local args = {
			[1] = "SyncMesh",
			[2] = {
				[1] = {
					["Part"] = part,
					["MeshId"] = "rbxassetid://"..meshid
				}
			}
		}
		_(args)
	end
	function SetTexture(part, texid)
		local args = {
			[1] = "SyncMesh",
			[2] = {
				[1] = {
					["Part"] = part,
					["TextureId"] = "rbxassetid://"..texid
				}
			}
		}
		_(args)
	end
	function SetName(part, stringg)
		local args = {
			[1] = "SetName",
			[2] = {
				[1] = workspace.Part
			},
			[3] = stringg
		}

		_(args)
	end
	function MeshResize(part,size)
		local args = {
			[1] = "SyncMesh",
			[2] = {
				[1] = {
					["Part"] = part,
					["Scale"] = size
				}
			}
		}
		_(args)
	end
	function Weld(part1, part2,lead)
		local args = {
			[1] = "CreateWelds",
			[2] = {
				[1] = part1,
				[2] = part2
			},
			[3] = lead
		}
		_(args)

	end
	function SetLocked(part,boolean)
		local args = {
			[1] = "SetLocked",
			[2] = {
				[1] = part
			},
			[3] = boolean
		}
		_(args)
	end
	function SetTrans(part,int)
		local args = {
			[1] = "SyncMaterial",
			[2] = {
				[1] = {
					["Part"] = part,
					["Transparency"] = int
				}
			}
		}
		_(args)
	end
	function CreateSpotlight(part)
		local args = {
			[1] = "CreateLights",
			[2] = {
				[1] = {
					["Part"] = part,
					["LightType"] = "SpotLight"
				}
			}
		}
		_(args)
	end
	function SyncLighting(part,brightness)
		local args = {
			[1] = "SyncLighting",
			[2] = {
				[1] = {
					["Part"] = part,
					["LightType"] = "SpotLight",
					["Brightness"] = brightness
				}
			}
		}
		_(args)
	end

	function Unanchor()
		for i,v in game.Workspace:GetDescendants() do
			spawn(function()
				SetLocked(v,false)
				SetAnchor(false,v)
			end)
		end
	end
	Unanchor()
end)

local f3x = Instance.new("TextButton")
f3x.Size = UDim2.new(0, 81,0, 34)
f3x.Position = UDim2.new(0.559, 0,0.146, 0)
f3x.BackgroundColor3 = Color3.new(0, 0, 0)
f3x.BorderSizePixel = 1
f3x.BorderColor3 = Color3.new(1, 0.741176, 0.133333)
f3x.Font = Enum.Font.SourceSans
f3x.Text = "Color Spam"
f3x.TextColor3 = Color3.new(1, 1, 1)
f3x.TextSize = 20
f3x.Parent = mainFrame

f3x.MouseButton1Click:Connect(function()
	local player = game.Players.LocalPlayer
	local char = player.Character
	local tool

	-- Search for "SyncAPI" in player and ReplicatedStorage
	for i, v in player:GetDescendants() do
		if v.Name == "SyncAPI" then
			tool = v.Parent
			break
		end
	end

	for i, v in game.ReplicatedStorage:GetDescendants() do
		if v.Name == "SyncAPI" then
			tool = v.Parent
			break
		end
	end

	-- Ensure that tool and remote are properly set
	if tool and tool:FindFirstChild("SyncAPI") then
		local remote = tool.SyncAPI.ServerEndpoint

		-- Function to invoke server
		local function _(args)
			remote:InvokeServer(unpack(args))
		end

		-- SetCollision Function
		local function SetCollision(part, boolean)
			local args = {
				[1] = "SyncCollision",
				[2] = {
					[1] = {
						["Part"] = part,
						["CanCollide"] = boolean
					}
				}
			}
			_(args)
		end

		-- SetAnchor Function
		local function SetAnchor(boolean, part)
			local args = {
				[1] = "SyncAnchor",
				[2] = {
					[1] = {
						["Part"] = part,
						["Anchored"] = boolean
					}
				}
			}
			_(args)
		end

		-- CreatePart Function
		local function CreatePart(cf, parent)
			local args = {
				[1] = "CreatePart",
				[2] = "Normal",
				[3] = cf,
				[4] = parent
			}
			_(args)
		end

		-- DestroyPart Function
		local function DestroyPart(part)
			local args = {
				[1] = "Remove",
				[2] = {
					[1] = part
				}
			}
			_(args)
		end

		-- MovePart Function
		local function MovePart(part, cf)
			local args = {
				[1] = "SyncMove",
				[2] = {
					[1] = {
						["Part"] = part,
						["CFrame"] = cf
					}
				}
			}
			_(args)
		end

		-- Resize Function
		local function Resize(part, size, cf)
			local args = {
				[1] = "SyncResize",
				[2] = {
					[1] = {
						["Part"] = part,
						["CFrame"] = cf,
						["Size"] = size
					}
				}
			}
			_(args)
		end

		-- AddMesh Function
		local function AddMesh(part)
			local args = {
				[1] = "CreateMeshes",
				[2] = {
					[1] = {
						["Part"] = part
					}
				}
			}
			_(args)
		end

		-- SetMesh Function
		local function SetMesh(part, meshid)
			local args = {
				[1] = "SyncMesh",
				[2] = {
					[1] = {
						["Part"] = part,
						["MeshId"] = "rbxassetid://"..meshid
					}
				}
			}
			_(args)
		end

		-- SetTexture Function
		local function SetTexture(part, texid)
			local args = {
				[1] = "SyncMesh",
				[2] = {
					[1] = {
						["Part"] = part,
						["TextureId"] = "rbxassetid://"..texid
					}
				}
			}
			_(args)
		end

		-- SetName Function
		local function SetName(part, stringg)
			local args = {
				[1] = "SetName",
				[2] = {
					[1] = part
				},
				[3] = stringg
			}
			_(args)
		end

		-- MeshResize Function
		local function MeshResize(part, size)
			local args = {
				[1] = "SyncMesh",
				[2] = {
					[1] = {
						["Part"] = part,
						["Scale"] = size
					}
				}
			}
			_(args)
		end

		-- Weld Function
		local function Weld(part1, part2, lead)
			local args = {
				[1] = "CreateWelds",
				[2] = {
					[1] = part1,
					[2] = part2
				},
				[3] = lead
			}
			_(args)
		end

		-- SetLocked Function
		local function SetLocked(part, boolean)
			local args = {
				[1] = "SetLocked",
				[2] = {
					[1] = part
				},
				[3] = boolean
			}
			_(args)
		end

		-- SetTrans Function
		local function SetTrans(part, int)
			local args = {
				[1] = "SyncMaterial",
				[2] = {
					[1] = {
						["Part"] = part,
						["Transparency"] = int
					}
				}
			}
			_(args)
		end

		-- CreateSpotlight Function
		local function CreateSpotlight(part)
			local args = {
				[1] = "CreateLights",
				[2] = {
					[1] = {
						["Part"] = part,
						["LightType"] = "SpotLight"
					}
				}
			}
			_(args)
		end

		-- SyncLighting Function
		local function SyncLighting(part, brightness)
			local args = {
				[1] = "SyncLighting",
				[2] = {
					[1] = {
						["Part"] = part,
						["LightType"] = "SpotLight",
						["Brightness"] = brightness
					}
				}
			}
			_(args)
		end

		-- Color Function
		local function Color(part, color)
			local args = {
				[1] = "SyncColor",
				[2] = {
					[1] = {
						["Part"] = part,
						["Color"] = color,
						["UnionColoring"] = false
					}
				}
			}
			_(args)
		end

		-- Randomize Function
		local function randomise()
			for i, v in game.Workspace:GetDescendants() do
				if v:IsA("BasePart") then
					spawn(function()
						SetLocked(v, false)
						Color(v, Color3.new(math.random(), math.random(), math.random()))
					end)
				end
			end
		end

		-- Run the randomization in a loop
		while wait() do
			spawn(function()
				randomise()
			end)
		end
	end

end)

local f3x = Instance.new("TextButton")
f3x.Size = UDim2.new(0, 316,0, 23)
f3x.Position = UDim2.new(0.058, 0,0.186, 0)
f3x.BackgroundColor3 = Color3.new(0, 0, 0)
f3x.BorderSizePixel = 1
f3x.BorderColor3 = Color3.new(1, 0.741176, 0.133333)
f3x.Font = Enum.Font.SourceSans
f3x.Text = "Delete Everything"
f3x.TextColor3 = Color3.new(1, 1, 1)
f3x.TextSize = 30
f3x.Parent = mainFrame

f3x.MouseButton1Click:Connect(function()
	local player = game.Players.LocalPlayer
	local char = player.Character
	local tool

	for i, v in player:GetDescendants() do
		if v.Name == "SyncAPI" then
			tool = v.Parent
			break
		end
	end

	for i, v in game.ReplicatedStorage:GetDescendants() do
		if v.Name == "SyncAPI" then
			tool = v.Parent
			break
		end
	end

	if tool and tool:FindFirstChild("SyncAPI") then
		local remote = tool.SyncAPI.ServerEndpoint

		local function _(args)
			remote:InvokeServer(unpack(args))
		end

		local function DestroyPart(part)
			local args = {
				[1] = "Remove",
				[2] = {
					[1] = part
				}
			}
			_(args)
		end

		local function DeleteAllParts()
			for _, part in pairs(workspace:GetDescendants()) do
				if part:IsA("BasePart") then
					spawn(function()
						DestroyPart(part)
					end)
				end
			end
		end

		DeleteAllParts()
	end
end)
