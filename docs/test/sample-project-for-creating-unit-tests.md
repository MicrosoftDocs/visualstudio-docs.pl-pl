---
title: Przykładowy kod dotyczący tworzenia testów jednostkowych
description: Ten artykuł zawiera przykładowy kod, który może być testowany z testów jednostkowych w programie Visual Studio.
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: sample
helpviewer_keywords:
- unit test sample [Visual Studio]
- unit tests, samples
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: deddf46a479e0ab8d4e0bebbaf3fffe4d90b622d
ms.sourcegitcommit: 0a8ac5f2a685270d9ca79bb39d26fd90099bfa29
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/09/2018
ms.locfileid: "51293450"
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

Aby pracować przy użyciu tego kodu, najpierw Utwórz projekt dla niego w programie Visual Studio. Postępuj zgodnie z instrukcjami, aby utworzyć projekt w [wskazówki: tworzenie i Uruchamianie testów jednostkowych dla kodu zarządzanego](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md#create-a-project-to-test).

## <a name="see-also"></a>Zobacz także

- [Przewodnik: Tworzenie i Uruchamianie testów jednostkowych dla kodu zarządzanego](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md)
- [Przewodnik: Używanie narzędzia testowania wiersza polecenia](https://msdn.microsoft.com/Library/52c11992-9e94-4067-a4b7-59f19d69d867)
