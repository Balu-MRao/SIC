
def deposit(amount):
    global n_500,n_200,n_100,amount_present
    n_500 = 100
    n_200 = 150
    n_100 = 200
    amount_present = (n_500 * 500) + (n_200 * 200) + (n_100 * 100)
    n_500_d, n_200_d, n_100_d = input('Enter the number of 500,200 and 100 notes:').split(' ')
    n_500_d = int(n_500)
    n_200_d = int(n_200)
    n_100_d = int(n_100)
    n_500 += n_500_d
    n_200 += n_200_d
    n_100 += n_100_d
    amount_present += amount
    return amount_present
def withdraw(withdraw_amount):
    remaining = 0
    if withdraw_amount % 100 == 0:
        print('Withdraw Succesfull!')
        if withdraw_amount > amount_present:
            print('Amount Exceeded')

        else:
            if withdraw_amount / 500 > n_500:
                notes_500 = n_500
                remaining = withdraw_amount - notes_500 * 500
                print('500 notes ', notes_500)

                if remaining / 200 > n_200:
                    notes_200 = n_200
                    remaining -= notes_200 * 200
                    print('200 notes ', notes_200)

                    notes_100 = remaining / 100
                    remaining -= notes_100 * 100
                    print('100 notes ', notes_100)
                    n_100 -= notes_100
                    print('Remaining 100 notes ', n_100 - notes_100)

                else:
                    notes_200 = remaining / 200

                    remaining -= notes_200 * 200
                    print('200 notes', notes_200)
                    print('Remaining 200 notes ', n_200 - notes_200)

            else:
                notes_500 = withdraw_amount / 500
                print('500 notes ', notes_500)
                print('Remaining 500 notes ', n_500 - notes_500)


    elif withdraw_amount >= 200 and withdraw_amount < 500:
        notes_200 = withdraw_amount / 200
        remaining = withdraw_amount - notes_200 * 200
        print('200 notes', notes_200)
        notes_100 = remaining / 100
        remaining -= notes_100 * 100
        print('100 notes ', notes_100)

    elif withdraw_amount >= 100 and withdraw_amount < 200:
        notes_100 = withdraw_amount / 100
        remaining = withdraw_amount - notes_100 * 100
        print('100 notes ', notes_100)

    else:
        print('Withdraw Unuccesfull!')
        print('Amount must be in multiples of 100 ')

    return remaining
while True:
     print('1.Deposit\n 2.Withdraw\n3.Check Amount Balance')
     n = int(input('Enter your choice:'))
     if n == 1:
         total_amount = int(input('Enter the amount to be deposit: '))
         d = deposit(total_amount)
         print('Total Amount Available in ATM is :', d)
     elif n == 2:
         with_amount = int(input('Enter the amount to withdrw:'))
         w=withdraw(with_amount)
         print('The Amount Available in ATM is :', w)
     elif n==3:
         print('Total Amount Available in ATM is :', amount_present)
     else:
         break
