__author__ = 'bknowlto'

import os, io, re
os.system('cls')

def getMatches():
    '''startingDirectory = 'C:\\Users\\bknowlto\\Documents'''''
    startingDirectory = raw_input("Where would you like to search (enter file path): ")
    searchString = raw_input("What string would you like to search for: ")

    os.chdir(startingDirectory)

    fileMatches = []
    for root, dirs, files in os.walk(startingDirectory):
        for file in files:
            recycleFolder = re.search('Recycle.Bin', root)
            if file.endswith(".sql") and not recycleFolder:
                filePath = os.path.join(root, file)
                f = open(filePath, 'r')
                fileData = f.read()
                f.close()
                match = re.search(searchString, fileData, re.IGNORECASE)
                if match:
                    print 'FOUND IN: ' + os.path.join(root, file)
                    fileMatches.append(os.path.join(root, file))

    return fileMatches

def viewMatchValues():
    fileMatches = getMatches()
    fileMatches.sort()
    viewSQLText(fileMatches)

def viewSQLText(fileMatches):
    print "\nHere are the files that have matches:"
    for i in range(0, len(fileMatches)):
        print "%d: %s" % (i+1, fileMatches[i])

    selection = raw_input("\nWhich sql file would you like to choose? (Enter the number to the left"
                          " of the path): ")
    print "Viewing %s\n\n" % (fileMatches[i-1])
    filePathCommand = 'type "%s"' % (fileMatches[i-1])
    print "\n"
    os.system(filePathCommand)

    menuSelection = menuChoice()
    if menuSelection.lower() == 'm':
        viewSQLText(fileMatches)

def menuChoice():
    menuChoiceValue = raw_input("\n\nPress M to view the files again or Q to quit:  ")
    return menuChoiceValue


viewMatchValues()