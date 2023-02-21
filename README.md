# check-schedule
# python
스케쥴은 i번째 일은 일을 처리하는데 정확히 Ti 시간이 걸리고 Si 시 내에 이 일을 처리하여야 한다는 것을 담고 있다. 0시부터 활동 2가지일을 동시에는 불가하다. 마감시간 내에 처리할 수 있는 범위 내에서 최대한 늦게 일을 시작할 수 있는 시간이 몇 시인지 출력하는 프로그램을 작성해보자! 0시에도 끝낼수 없다면 -1출력해라


Num=int(input())
schedules=[]
for _ in range(Num):
    T,S = map(int, input().split())
    schedules.append([T,S])
schedules = sorted(schedules, key=lambda x:x[1]) #완료순으로 
time=0 #시작시간
while 1:
    sumTime=time #전체 일정들에 대해
    for t, s in schedules:
        if sumTime+t<= s: #제시간안에 처리 가능하면
            sumTime+=t 
        else: #늦게 시작했는데 완료x
            print(time-1) #시작시간보다 1시간 일찍 
            exit() #while문 종료
    time+= 1
