# pynewman_one
"""
    作者：陆耀锴
    版本：1.0
    日期：18/2/2019
    功能：输入某年某月某日，判断这一天是这年的第几天？
    2.0:使用列表替换元祖
    3.0:新增功能:将月份划分为不同的集合在操作
    4.0:将月份及其对应天数通过字典表示
"""

from datetime import datetime

def is_leap_year(year):
    """
        判断year是否为闰年
        是返回ture
        否返回false
    """

    is_leap = False
    if (year % 400 == 0) or ((year % 4 == 0) and (year % 100 != 0)):
        is_leap = True
    return is_leap

def main():
    """
        主函数
    """
    input_date_str = input('请输入日期(yyyy/mm/dd):')
    input_date = datetime.strptime(input_date_str,'%Y/%m/%d')
    print(input_date)

    year = input_date.year
    month = input_date.month
    day = input_date.day

    _30_days_month_set = {4,6,9,11}
    _31_days_month_set = {1,3,5,7,8,10,12}

    days = 0
    days += day

    for i in range(1,month):
        if i in _30_days_month_set:
            days += 30
        elif i in _31_days_month_set:
            days += 31
        elif month > 2:
            days += 28

    if is_leap_year(year) and month > 2:
        days += 1

    # day_in_month_list = [31,28,31,30,31,30,31,31,30,31,30,31]
    # if is_leap_year(year):
    #     day_in_month_list[1] = 29
    # days = sum(day_in_month_list[:month - 1]) + day

    print(('这是第{}天').format(days))

if __name__ == '__main__':
    main()





