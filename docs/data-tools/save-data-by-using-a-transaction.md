---
title: 'Instrukcje: zapisywanie danych przy użyciu transakcji'
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
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: beadb43d7eed78f04fc60ce1307045e9badac205
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75586279"
---
# <a name="how-to-save-data-by-using-a-transaction"></a>Instrukcje: zapisywanie danych przy użyciu transakcji

Dane są zapisywane w transakcji przy użyciu przestrzeni nazw <xref:System.Transactions>. Użyj obiektu <xref:System.Transactions.TransactionScope>, aby wziąć udział w transakcji, która jest automatycznie zarządzana.

Projekty nie są tworzone z odwołaniem do zestawu *System. Transactions* , więc musisz ręcznie dodać odwołanie do projektów, które używają transakcji.

Najprostszym sposobem implementacji transakcji jest utworzenie wystąpienia obiektu <xref:System.Transactions.TransactionScope> w instrukcji `using`. (Aby uzyskać więcej informacji, zobacz [using instrukcji](/dotnet/visual-basic/language-reference/statements/using-statement)and [using](/dotnet/csharp/language-reference/keywords/using-statement).) Kod, który jest uruchamiany w instrukcji `using` uczestniczy w transakcji.

Aby zatwierdzić transakcję, wywołaj metodę <xref:System.Transactions.TransactionScope.Complete%2A> jako ostatnią instrukcję w bloku using.

Aby wycofać transakcję, Zgłoś wyjątek przed wywołaniem metody <xref:System.Transactions.TransactionScope.Complete%2A>.

## <a name="to-add-a-reference-to-the-systemtransactionsdll"></a>Aby dodać odwołanie do elementu System. Transactions. dll

1. W menu **projekt** wybierz polecenie **Dodaj odwołanie**.

2. Na karcie **.NET** (**SQL Server** karcie Projekty SQL Server) wybierz pozycję **System. Transactions**, a następnie wybierz przycisk **OK**.

     Odwołanie do *System. Transactions. dll* jest dodawane do projektu.

## <a name="to-save-data-in-a-transaction"></a>Aby zapisać dane w transakcji

- Dodaj kod, aby zapisać dane w instrukcji using zawierającej transakcję. Poniższy kod pokazuje, jak utworzyć i utworzyć wystąpienie obiektu <xref:System.Transactions.TransactionScope> w instrukcji using:

     [!code-vb[VbRaddataSaving#11](../data-tools/codesnippet/VisualBasic/save-data-by-using-a-transaction_1.vb)]
     [!code-csharp[VbRaddataSaving#11](../data-tools/codesnippet/CSharp/save-data-by-using-a-transaction_1.cs)]

## <a name="see-also"></a>Zobacz także

- [Zapisywanie danych z powrotem w bazie danych](../data-tools/save-data-back-to-the-database.md)
- [Przewodnik: Zapisywanie danych w transakcji](../data-tools/save-data-in-a-transaction.md)
