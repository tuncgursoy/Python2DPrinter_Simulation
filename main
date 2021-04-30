

# Turnin logo 90 degree clockwise
def Turn90(command):
    temp = ""
    switcher = {
        'U': 'R',
        'D': 'L',
        'R': 'D',
        'L': 'U',
    }
    for i in command:
        temp += switcher.get(i)
    return temp


# To find equality check
def CalculatePoint(command, locx, locy):
    temp = 0
    switcher = {
        'U': -2,
        'D': 2,
        'R': 2,
        'L': -2,
    }
    currentx = locx * 2
    currenty = locy * 2
    two2DArray = [[0 for i in range(21)] for j in range(21)]
    for i in command:
        if (i == 'U' or i == 'D'):
            currenty = (currenty + switcher.get(i)) % (21)
            if (i == 'U'):
                two2DArray[(currenty + 1) % 21][currentx] = 1
            else:
                two2DArray[(currenty - 1) % 21][currentx] = 1
        else:
            currentx = (currentx + switcher.get(i)) % (21)
            if (i == 'R'):
                two2DArray[currenty][(currentx - 1) % 21] = 1
            else:
                two2DArray[currenty][(currentx + 1) % 21] = 1
    for i in range(0, 21):
        for j in range(0, 21):
            temp = temp + two2DArray[i][j] * (j ** 2) + (13 ** i)
    return temp


class Logos:
    listofLogos = []

    def appendToList(self, newlogo):

        if (self.findReqLogo(newlogo.getName()) != "pass"):
            return False
        else:
            self.listofLogos.append(newlogo)
            return True

    def findReqLogo(self, nameOfRequested):
        for i in self.listofLogos:
            if (i.getName() == nameOfRequested):
                return i
        return "pass"


class Logo:
    matrix = [[" " for i in range(21)] for j in range(21)]
    given_command = ""
    name = ""

    def __init__(self, Command, name):
        self.given_command = Command
        self.name = name

    def getGiven_command(self):
        return self.given_command

    def getName(self):
        return self.name

    def isItSame(self, otherLogo):
        for x in range(11):
            for y in range(11):
                if (CalculatePoint(self.getGiven_command(), 0, 0) == CalculatePoint(otherLogo.getGiven_command(), x,
                                                                                    y)):
                    return True
                elif (CalculatePoint(self.getGiven_command(), 0, 0) == CalculatePoint(
                        Turn90(otherLogo.getGiven_command()), x, y)):
                    return True
                elif (CalculatePoint(self.getGiven_command(), 0, 0) == CalculatePoint(
                        Turn90(Turn90(otherLogo.getGiven_command())), x, y)):
                    return True
                elif (CalculatePoint(self.getGiven_command(), 0, 0) == CalculatePoint(
                        Turn90(Turn90(Turn90(otherLogo.getGiven_command()))), x, y)):
                    return True
        return False

    def engrave(self, x, y):
        self.matrix = [[" " for i in range(21)] for j in range(21)]
        switcher = {
            'U': '|',
            'D': '|',
            'R': '-',
            'L': '-',
        }
        for x1 in range(0, 21, 2):
            for y1 in range(0, 21, 2):
                self.matrix[y1][x1] = "."
        currentLoc = {"x": x + (x - 2), "y": y + (y - 2)}
        for i in self.getGiven_command():
            if (i == 'U'):
                self.matrix[currentLoc["y"] % 21][(currentLoc["x"] - 1) % 21] = switcher.get(i)
                currentLoc["x"] -= 2
            elif (i == 'D'):
                self.matrix[currentLoc["y"] % 21][(currentLoc["x"] + 1) % 21] = switcher.get(i)
                currentLoc["x"] += 2
            elif (i == 'R'):
                self.matrix[(currentLoc["y"] + 1) % 21][currentLoc["x"] % 21] = switcher.get(i)
                currentLoc["y"] += 2
            elif (i == 'L'):
                self.matrix[(currentLoc["y"] - 1) % 21][currentLoc["x"] % 21] = switcher.get(i)
                currentLoc["y"] -= 2
            else:
                print("Undifined Command in Given Command " + i)

        for x2 in range(0, 21):
            for y2 in range(0, 21):
                print(self.matrix[y2][x2], end='')
            print()
        print()


switcher = {
    'LOGO': 1,
    'SAME': 2,
    'ENGRAVE': 3
}
list = Logos()
while (True):
    try:
        cmd = input()
        cmdarr = cmd.split()
        if (1 == switcher.get(cmdarr[0].upper())):
            if (list.appendToList(Logo(cmdarr[2], cmdarr[1]))):
                print('{0} defined'.format(cmdarr[1]))
            else:
                print('{0} Already defined'.format(cmdarr[1]))
        elif (2 == switcher.get(cmdarr[0].upper())):
            if (list.findReqLogo(cmdarr[1]) != "pass" and list.findReqLogo(cmdarr[2]) != "pass"):
                if (list.findReqLogo(cmdarr[1]).isItSame(list.findReqLogo(cmdarr[2]))):
                    print("Yes")
                else:
                    print("No")
            else:
                print('{0} or {1} is not exists in database'.format(cmdarr[1], cmdarr[2]))
        elif (3 == switcher.get(cmdarr[0].upper())):
            if (list.findReqLogo(cmdarr[1]) != "pass"):
                list.findReqLogo(cmdarr[1]).engrave(int(cmdarr[2]), int(cmdarr[3]))
            else:
                print('{0} is not defined'.format(cmdarr[1]))
        elif (cmdarr[0].upper() == "EXIT" or cmdarr[0].upper() == "EXİT"):
            break
        elif (cmdarr[0].upper() == "HELP"):
            print(
                "Commands:\nLOGO -> LOGO name_of_logo Def_lOGO\nSAME -> Same NameOfLogo1 NameOfLogo2\nENGRAVE -> ENGRAVE name_of_logo x_coordinate y_coordinate\nExit -> Exits from the program")
        else:
            print("Undefined Command")
    except EOFError:
        break










