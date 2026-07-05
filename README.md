local ReplicatedStorage = game:GetService("ReplicatedStorage")
local ServerBrowser = ReplicatedStorage:WaitForChild("__ServerBrowser")

local ServerIDs = {
    "571ef504-ccf3-41cc-b790-6bd696098b96",
    "7f1e7fd3-d498-4280-9274-15e2e94fcd12",
    "bf71482c-412a-4497-bc0b-a41b26893177",
    "151515ca-fb19-4baf-be6b-00d17c55fbc9"
    "f7296393-184f-4351-a245-f44a4e163820"
}

local function ServerHop()
    local AvailableServers = {}
    
    for _, id in ipairs(ServerIDs) do
        if id ~= game.JobId then
            table.insert(AvailableServers, id)
        end
    end

    if #AvailableServers > 0 then
        local TargetServer = AvailableServers[math.random(1, #AvailableServers)]
        ServerBrowser:InvokeServer("teleport", TargetServer)
    else
        warn("Nenhum servidor alternativo encontrado.")
    end
end

ServerHop()
