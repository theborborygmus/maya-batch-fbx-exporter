#run this code on a maya file that is in directory that contains the animation files intended for export
import os
import maya.cmds as cmds
import pymel.core as pm

#finds all other files in directory.
dir = os.path.dirname(cmds.file(q = True, sn = True))
allfiles = os.listdir(dir)
export = []

#this creates a list of the maya files intended for export; in this case following the naming convention: 'Suffix_' 
for i in allfiles:
    if 'Suffix_' in i:
        export.append(i)

#iterates through the maya files and exports FBXs to the same directory using the name of the export file
for i in export:
    cmds.file(i, open=True, force=True) 
    pm.select ( 'root' , r = True)
    filename = i.split('.')
    filepath = dir+'/'+filename[0]+'.fbx' 
    print('Exported-------', filepath)
    cmds.file(filepath, force=True, options="v=0;", type="FBX export", exportSelected=True)
    
print('------------DONE------------')
