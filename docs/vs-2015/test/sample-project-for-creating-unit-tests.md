---
title: Przykładowy projekt do tworzenia testów jednostkowych | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
helpviewer_keywords:
- unit test sample [Visual Studio]
- unit tests, samples
ms.assetid: db80aaf2-0652-4d3f-a8c5-2a98fd8502a2
caps.latest.revision: 32
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: d495d0bf12c900d34a04a84e950b002494b7b5c3
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72660393"
---
# <a name="sample-project-for-creating-unit-tests"></a>Przykładowy projekt dotyczący tworzenia testów jednostkowych
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ten przykładowy kod jest przeznaczony do użycia w następujących przewodnikach:

- [Przewodnik: Tworzenie i uruchamianie testów jednostkowych dla kodu zarządzanego](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md). Ten przewodnik przeprowadzi Cię przez kroki tworzenia i dostosowywania testów jednostkowych, uruchamiania ich oraz badania wyników testów.

- [Przewodnik: uruchamianie testów i wyświetlanie pokrycia kodu](https://msdn.microsoft.com/d4aab8e2-2140-4975-b4e3-41ef3fa944c8). W tym instruktażu przedstawiono sposób wyświetlania danych pokrycia kodu, które pokazują udział testowanego kodu projektu.

- [Przewodnik: Używanie narzędzia testowego wiersza polecenia](https://msdn.microsoft.com/library/52c11992-9e94-4067-a4b7-59f19d69d867). W tym instruktażu użyjesz narzędzia wiersza polecenia MSTest. exe, aby uruchomić testy i wyświetlić wyniki.

## <a name="sample-code"></a>Przykładowy kod
 Jedynym zamierzonym błędem w tym przykładzie jest to, że w metodzie Debet "m_balance + = kwota" powinna być znak minus nie jest znakiem plus przed znakiem równości.

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

 /* Przykładowe firmy, organizacje, produkty, nazwy domen, adresy e-mail, logo, osoby, miejsca i zdarzenia opisane w niniejszym dokumencie są fikcyjne.  Żadne powiązania z rzeczywistymi firmami, organizacjami, produktami, nazwami domen, adresami e-mail, logo, osobami, miejscami lub zdarzeniami nie są zamierzone ani wywnioskowane. \*/

## <a name="working-with-the-code"></a>Praca z kodem
 Aby można było korzystać z tego kodu, należy najpierw utworzyć projekt dla niego w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Wykonaj kroki opisane w sekcji "Przygotowanie przewodnika" w [przewodniku: Tworzenie i uruchamianie testów jednostkowych dla kodu zarządzanego](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md).

## <a name="see-also"></a>Zobacz też
 [Przewodnik: Tworzenie i uruchamianie testów jednostkowych dla przewodnika po kodzie zarządzanym](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md) [: uruchamianie testów i wyświetlanie](https://msdn.microsoft.com/d4aab8e2-2140-4975-b4e3-41ef3fa944c8) przewodnika dotyczącego pokrycia kodu [: korzystanie z narzędzia testowego wiersza polecenia](https://msdn.microsoft.com/library/52c11992-9e94-4067-a4b7-59f19d69d867)
