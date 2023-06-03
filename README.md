# VersionChecker
VersionChecker For My FiveM (cfx.re) Resources


# How To Setup UpdateChecker
# Step 1 - Create A txt File In VersionChecker Resource/File
# Step 2 - Create A Server Side file And Add This Below
# Step 3 - Update FILE_NAME.txt On Line 11 To The txt Created
# Step 4 - Update local resourcename To The Resource Name 
# Step 5 - Update local howto To Your Howto Update
# Step 6 - Match The Version In The txt To The Version In FxMani
# Step 7 - Test The Resource And The Update Checker


```lua
local function CheckVersion()
    PerformHttpRequest('https://raw.githubusercontent.com/Marshxan/VersionChecker/master/FILE_NAME.txt', function(err, newestVersion, headers)
    	local currentVersion = GetResourceMetadata(GetCurrentResourceName(), 'version')
        local resourcename = "RESOURCE_NAME_HERE"
        local howto = "Please Contact FrostyyDevs For A Update"
    	if not newestVersion then 
            print("Currently unable to run a version check.") 
            return 
        end

    	local advice = "^1You Are Currently Running A Outdated Version Of "..resourcename.."\n "..howto.." ^7"
    	if newestVersion:gsub("%s+", "") == currentVersion:gsub("%s+", "") 
        then advice = '^6You are running the latest version.^7'
        else 
            print("")
            print("")
            print("^3Version Check^7: ^2Current^7: "..currentVersion.." ^2Latest^7: "..newestVersion)
            print("")
            print("")
        end
        print("")
    	print(advice)
        print("")
    end)
end
CheckVersion()
```