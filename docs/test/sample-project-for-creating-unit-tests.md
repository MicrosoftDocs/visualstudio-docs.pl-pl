---
title: Przykładowy kod dotyczący tworzenia testów jednostkowych
description: Ten artykuł zawiera przykładowy kod, który może być testowany z testów jednostkowych w programie Visual Studio.
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: sample
helpviewer_keywords:
- unit test sample [Visual Studio]
- unit tests, samples
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 172cf928c52f31f650337c5f0d449e28ccecc294
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "55018530"
---
# <a name="sample-code-for-testing"></a>Przykładowy kod do testowania

Ten przykładowy kod zawiera klasę *BankAccount*, za pomocą różnych metod, które mogą być testowane za pomocą testów jednostkowych.

Kod jest używany w poniższych instruktażach:

- [Tworzenie i Uruchamianie testów jednostkowych dla kodu zarządzanego](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md). Ten instruktaż poprowadzi Cię przez kroki, aby utworzyć i dostosować testy jednostkowe, uruchamiać je i sprawdź wyniki testu.
- [Użyj narzędzia testowania wiersza polecenia](https://msdn.microsoft.com/Library/52c11992-9e94-4067-a4b7-59f19d69d867). W tym przewodniku używamy *MSTest.exe* narzędzie wiersza polecenia, aby uruchomić testy i wyświetlić wyniki.

## <a name="sample-code"></a>Przykładowy kod

Tylko celowy błąd, w tym przykładzie jest w metody Debet "m_balance += amount" powinien minus nie znakiem plus, zaloguj się przed równości.

```csharp
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

/ * Przykładowe firmy, organizacje, produkty, nazwy domen, adresy e-mail, logo, osoby, miejsca i zdarzenia wymienione w niniejszym dokumencie są fikcyjne. Wszelkie rzeczywistą firmą, organizacji, produktu, nazwy domeny, adres e-mail, logo, osoby, miejsca lub zdarzeń jest przeznaczone i powinno być wnioskowane. \*/

## <a name="create-the-project"></a>Utwórz projekt

Aby pracować przy użyciu tego kodu, najpierw Utwórz projekt dla niego w programie Visual Studio. Postępuj zgodnie z instrukcjami, aby utworzyć projekt w [instruktażu: Tworzenie i Uruchamianie testów jednostkowych dla kodu zarządzanego](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md#create-a-project-to-test).

## <a name="see-also"></a>Zobacz także

- [Przewodnik: Tworzenie i Uruchamianie testów jednostkowych dla kodu zarządzanego](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md)
- [Przewodnik: Użyj narzędzia testowania wiersza polecenia](https://msdn.microsoft.com/Library/52c11992-9e94-4067-a4b7-59f19d69d867)
