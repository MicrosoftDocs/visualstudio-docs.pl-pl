---
title: Przykładowy projekt dotyczący tworzenia testów jednostkowych | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
helpviewer_keywords:
- unit test sample [Visual Studio]
- unit tests, samples
ms.assetid: db80aaf2-0652-4d3f-a8c5-2a98fd8502a2
caps.latest.revision: 32
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 67ebbde52facf50eff534322d85a926968acdf0d
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65705960"
---
# <a name="sample-project-for-creating-unit-tests"></a>Przykładowy projekt dotyczący tworzenia testów jednostkowych
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ten przykładowy kod znajduje się do użytku w poniższych instruktażach:  
  
- [Przewodnik: Tworzenie i Uruchamianie testów jednostkowych dla kodu zarządzanego](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md). Ten instruktaż poprowadzi Cię przez kroki, aby utworzyć i dostosować testy jednostkowe, uruchamiać je i sprawdź wyniki testu.  
  
- [Przewodnik: Uruchom testy, aby wyświetlić pokrycia kodu](https://msdn.microsoft.com/d4aab8e2-2140-4975-b4e3-41ef3fa944c8). W tym instruktażu przedstawiono sposób wyświetlania danych pokrycia kodu, który zawiera część kodu projektu, który jest poddawana testom.  
  
- [Wskazówki: Korzystanie z narzędzia testu wiersza polecenia](https://msdn.microsoft.com/library/52c11992-9e94-4067-a4b7-59f19d69d867). W tym przewodniku umożliwia narzędzie wiersza polecenia MSTest.exe przeprowadzać testy i przeglądać wyniki.  
  
## <a name="sample-code"></a>Przykładowy kod  
 Tylko celowy błąd, w tym przykładzie jest w metody Debet "m_balance += amount" powinien minus nie znakiem plus, zaloguj się przed równości.  
  
```  
using System;   
  
namespace BankAccountNS  
{  
    /// <summary>   
    /// Bank Account demo class.   
    /// </summary>   
    public class BankAccount  
    {  
        private string m_customerName;  
  
        private double m_balance;  
  
        private bool m_frozen = false;  
  
        private BankAccount()  
        {  
        }  
  
        public BankAccount(string customerName, double balance)  
        {  
            m_customerName = customerName;  
            m_balance = balance;  
        }  
  
        public string CustomerName  
        {  
            get { return m_customerName; }  
        }  
  
        public double Balance  
        {  
            get { return m_balance; }  
        }  
  
        public void Debit(double amount)  
        {  
            if (m_frozen)  
            {  
                throw new Exception("Account frozen");  
            }  
  
            if (amount > m_balance)  
            {  
                throw new ArgumentOutOfRangeException("amount");  
            }  
  
            if (amount < 0)  
            {  
                throw new ArgumentOutOfRangeException("amount");  
            }  
  
            m_balance += amount; // intentionally incorrect code  
        }  
  
        public void Credit(double amount)  
        {  
            if (m_frozen)  
            {  
                throw new Exception("Account frozen");  
            }  
  
            if (amount < 0)  
            {  
                throw new ArgumentOutOfRangeException("amount");  
            }  
  
            m_balance += amount;  
        }  
  
        private void FreezeAccount()  
        {  
            m_frozen = true;  
        }  
  
        private void UnfreezeAccount()  
        {  
            m_frozen = false;  
        }  
  
        public static void Main()  
        {  
            BankAccount ba = new BankAccount("Mr. Bryan Walton", 11.99);   
  
            ba.Credit(5.77);  
            ba.Debit(11.22);  
            Console.WriteLine("Current balance is ${0}", ba.Balance);  
        }  
  
    }  
}  
```  
  
 / * Przykładowe firmy, organizacje, produkty, nazwy domen, adresy e-mail, logo, osoby, miejsca i zdarzenia wymienione w niniejszym dokumencie są fikcyjne.  Wszelkie rzeczywistą firmą, organizacji, produktu, nazwy domeny, adres e-mail, logo, osoby, miejsca lub zdarzeń jest przeznaczone i powinno być wnioskowane. \*/  
  
## <a name="working-with-the-code"></a>Praca z kodem  
 Aby pracować przy użyciu tego kodu, najpierw należy utworzyć projekt dla niego w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Postępuj zgodnie z instrukcjami w sekcji "Przygotowanie instruktażu" [instruktażu: Tworzenie i Uruchamianie testów jednostkowych dla kodu zarządzanego](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik: Tworzenie i Uruchamianie testów jednostkowych dla kodu zarządzanego](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md)   
 [Przewodnik: Uruchom testy, aby wyświetlić pokrycia kodu](https://msdn.microsoft.com/d4aab8e2-2140-4975-b4e3-41ef3fa944c8)   
 [Wskazówki: Korzystanie z narzędzia testu wiersza polecenia](https://msdn.microsoft.com/library/52c11992-9e94-4067-a4b7-59f19d69d867)
