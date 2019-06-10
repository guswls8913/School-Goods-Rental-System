# School-Goods-Rental-System

class Queue:
    def __init__(self):
        self.items = []
    def enqueue(self, item):
        self.items.insert(0, item)
    def dequeue(self):
        a = self.items.pop()
        return a
    def isEmpty(self):
        return len(self.items) == []
    def size(self):
        return len(self.items)
    def queuer(self):
        return self.items

main_data={}
origin_data={}
student={}
sp = '0000'
f = '종료'

def 물품등록():
    print('물품등록을 원하신다면 비밀번호를 입력해주세요')
    while True :
        p=input()
        if p == sp:
            print('잠금해제. 물품 등록 시작. 물품 등록을 멈추시려면 "종료 0"을 입력해주세요')
            while True:
                a=input_func()
                if a[0] =='종료':
                    print('정말로 종료하시겠습니까? 종료하시려면 "종료"를 입력해주세요')
                    break
                else:
                    main_data[a[0]]=a[1]
                    origin_data[a[0]]=a[1]
        elif p == f :
            break
        else:
            print('비밀번호가 틀렸습니다')

q = Queue()
q.__init__()           

def 대여or반납():
    while True:
        mode_num=input('대여시 1, 반납시 2, 현재 상태 확인시 3, 종료시 4를 입력하세요')    
        if mode_num=='1':
            print('학번을 입력하세요')
            d = input()
            q.enqueue(d)
            a=input_func()
            if a[0] not in main_data:
                print('그런 것은 없습니다')
            elif main_data[a[0]]-a[1]<0:
                print('보유한 것보다 많습니다')
            else:
                main_data[a[0]]-=a[1]
        elif mode_num=='2':
            a=input_func()
            if a[1]+main_data[a[0]] > origin_data[a[0]]:
                print('수량을 재확인 하세요')
            else:
                main_data[a[0]]+=a[1]
        elif mode_num=='3':
            print(main_data)
        elif mode_num=='4':
            break
        else:
            print('입력이 잘못되었습니다.')

def 학번확인():
    n = 0
    print('학번을 입력하세요')
    b = input()
    for i in q.items:
        if i == b:
            n = n+1
    print(n)


def input_func():
    a,b=input().split(' ')
    list1=[a,int(b)]
    return list1
    
    
    
물품등록()

대여or반납()

학번확인()
