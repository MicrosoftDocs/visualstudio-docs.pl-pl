---
title: 'Instrukcje: Zapisywanie danych przy użyciu transakcji'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- saving data, using transactions
- System.Transactions namespace
- transactions, saving data
- data [Visual Studio], saving
ms.assetid: 8b835e8f-34a3-413d-9bb5-ebaeb87f1198
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 8d5d47cfc21b0aebef884fade422600be2beeb58
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55924373"
---
# <a name="how-to-save-data-by-using-a-transaction"></a>Instrukcje: Zapisywanie danych przy użyciu transakcji

Zapisywanie danych w ramach transakcji przy użyciu <xref:System.Transactions> przestrzeni nazw. Użyj <xref:System.Transactions.TransactionScope> obiekt, aby uczestniczyć w transakcji, które są zarządzane automatycznie dla Ciebie.

Projekty nie są tworzone za pomocą odwołania do *System.Transactions* zestawu, więc trzeba ręcznie dodać odwołania do projektów, które korzystają z transakcji.

Najłatwiejszym sposobem realizowania transakcji jest utworzenie wystąpienia <xref:System.Transactions.TransactionScope> obiektu `using` instrukcji. (Aby uzyskać więcej informacji, zobacz [za pomocą instrukcji](/dotnet/visual-basic/language-reference/statements/using-statement), i [za pomocą instrukcji](/dotnet/csharp/language-reference/keywords/using-statement).) Kod, który jest uruchamiany w ramach `using` instrukcji bierze udział w transakcji.

Aby zatwierdzić transakcji, należy wywołać <xref:System.Transactions.TransactionScope.Complete%2A> block metodę jako ostatnią instrukcję w przy użyciu.

Aby wycofać transakcji zgłoszenie wyjątku przed wywołaniem <xref:System.Transactions.TransactionScope.Complete%2A> metody.

## <a name="to-add-a-reference-to-the-systemtransactionsdll"></a>Aby dodać odwołanie do System.Transactions.dll

1.  Na **projektu** menu, wybierz opcję **Dodaj odwołanie**.

2.  Na **.NET** kartę (**programu SQL Server** kartę dla projektów programu SQL Server), wybierz opcję **System.Transactions**, a następnie wybierz pozycję **OK**.

     Odwołanie do *System.Transactions.dll* zostanie dodany do projektu.

## <a name="to-save-data-in-a-transaction"></a>Aby zapisać dane w ramach transakcji

-   Dodaj kod, aby zapisać dane w obrębie za pomocą instrukcji, która zawiera transakcji. Poniższy kod przedstawia sposób tworzenia i utworzyć wystąpienie <xref:System.Transactions.TransactionScope> obiektu w za pomocą instrukcji:

     [!code-vb[VbRaddataSaving#11](../data-tools/codesnippet/VisualBasic/save-data-by-using-a-transaction_1.vb)]
     [!code-csharp[VbRaddataSaving#11](../data-tools/codesnippet/CSharp/save-data-by-using-a-transaction_1.cs)]

## <a name="see-also"></a>Zobacz także

- [Zapisywanie danych z powrotem w bazie danych](../data-tools/save-data-back-to-the-database.md)
- [Przewodnik: Zapisywanie danych w ramach transakcji](../data-tools/save-data-in-a-transaction.md)