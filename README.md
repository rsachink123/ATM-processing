# ATM-related transactions through Python coding

from time import*
class BankAccount:
    def __init__(self, balance=5000):
        self.balance = balance
    def deposit(self, value):
        self.balance = self.balance+value
        print('Your current amount is', self.balance)
    def withdraw(self, value):
        self.balance = self.balance-value
        print('Your current amount is', self.balance)
class SavingAccount(BankAccount):
    def __init__(self, balance=5000):
        self.balance = balance
    def deposit(self, value):
        self.balance = self.balance+value
        print('Your current amount is', self.balance)
class CurrentAccount(BankAccount):
    def __init__(self, balance=5000):
        self.balance = balance
    def withdraw(self, value):
        if value>1000:
            print('You can not withdraw more than 1000')
        else:
            self.balance=self.balance-value
            print('Your current amount is', self.balance)
class TransferMoney(BankAccount):
    def __init__(self, balance=5000):
        self.balance=balance
    def transfer(self, value):
        if value<1000:
            print('you can not transfer money.You have low balance.')
        else:
            self.balance=self.balance-value
            print('The current ammount is', self.balance)
SA = SavingAccount()
CA = CurrentAccount()
TM = TransferMoney()
print("Please insert your card")
print('Wait for processing...')
sleep(3)

n = int(input("Please enter 1 for English:"))
if n==1:
    n1 = input("Please enter your 2 digit pin number:")
    if len(n1)==2:
        while True:
            print('1.Saving Account')
            print('2.Current Account')
            print()
            Mainopt = int(input('Please enter your choice:'))
            if Mainopt==1:
                print('1.Transfer')
                print('2.Balance enquiry')
                print('3.Deposit')
                print('4.Withdraw')
                print()
                Subopt = int(input("Please enter your choice:"))
                if Subopt==1:
                    print('Your current balance is', SA.balance)
                    print('The minimum balance to be maintained is 1000.')
                    print('Please enter the 4 digit account number in which you want to transfer the money.')
                    accno = input('To Account:')
                    
                    if len(accno)==4:
                        value = int(input('Please enter your amount:'))
                        if SA.balance-value>=1000:
                            
                            print('Wait for processing...')
                            sleep(2)
                            
                            print("Congrats,you have completed your transaction.")
                            TM.withdraw(value)
                        else:
                            print('Sorry, you have not enough balance for transaction.')
                    else:
                        print("Sorry,You have entered invalid account number.Please try again.")
                elif Subopt==2:
                    print('Your current amount is', SA.balance)
                elif Subopt ==3:
                    value = int(input('Please enter your amount for deposit in your saving account:'))
                    SA.deposit(value)
                    print("You have completed your transaction.")
                elif Subopt==4:
                    value = int(input('Please enter your amount:'))
                    CA.withdraw(value)
                    print("You have completed your transaction.")
                else:
                    print('You have entered invalid number.Please try again with valid number')
            elif Mainopt == 2:
                print('1.Transfer')
                print('2.Balance enquiry')
                print('3.Deposit')
                print('4.Withdraw')
                print()
                Subopt = int(input('Please enter your choice:'))
                if Subopt==1:
                    print('Your current balance is', CA.balance)
                    print('The minimum balance to be maintained is 1000.')
                    print('Please enter the 4 digit account number in which you want to transfer the money.')
                    accno = input('To Account:')
                    
                    
                    if len(accno)==4:
                        value = int(input('Please enter your amount:'))
                        if TM.balance-value>=1000:
                            print('Wait for processing...')
                            sleep(2)
                            print("Congrats,you have completed your transaction.")
                            TM.withdraw(value)
                        else:
                            print('Sorry, you have not enough balance for transaction.')
                    else:
                        print("Sorry,You have entered invalid account number.Please try again.")
                elif Subopt==2:
                    print('Your current amount is', CA.balance)
                elif Subopt == 3:
                    value = int(input("Please enter your amount for deposit in current account:"))
                    CA.deposit(value)
                    print("You have completed your transaction.")
                elif Subopt==4:
                    value = int(input("Please enter your amount for withdraw from current account:"))
                    CA.withdraw(value)
                    print("You have completed your transaction.")
                else:
                    print('--##You have entered wrong choice.Please try again with valid choice.')
            else:
                print('You have entered wrong choice.Please enter valid choice.')
            break
            
    else:
        print("You have entered wrong pin number.Please try again.")
else:
    print("You have entered wrong choice.Please try again.")
print("Thank you for choosing us.")     
