import os
from building import *
Import('rtconfig')

src   = []
cwd   = GetCurrentDir()

dialect = ''
dialects = next(os.walk(cwd))[1]
try:
    dialects.remove('message_definitions')
    dialects.remove('.git')
    dialects.remove('.vscode')
except:
    pass
    
for d in dialects:
    if GetDepend('PKG_USING_MAVLINK_DIALECT_' + d):
        dialect = d
        break

# add include path.
path  = [cwd, cwd + '/' + dialect]

# add src and include to group.
group = DefineGroup('mavlink', src, depend = ['PKG_USING_MAVLINK'], CPPPATH = path)

Return('group')
