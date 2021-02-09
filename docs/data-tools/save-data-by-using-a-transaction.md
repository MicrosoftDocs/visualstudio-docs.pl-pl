---
title: 'Instrukcje: zapisywanie danych przy użyciu transakcji'
description: Zapoznaj się z tematem zapisywanie danych przy użyciu transakcji z narzędziami zestawu danych w programie Visual Studio. Dane są zapisywane w transakcji przy użyciu przestrzeni nazw System. Transactions.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
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
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: c633ed01821f500e958d3c7549febc23cf33c09d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99858491"
---
# <a name="how-to-save-data-by-using-a-transaction"></a>Instrukcje: zapisywanie danych przy użyciu transakcji

Dane są zapisywane w transakcji przy użyciu <xref:System.Transactions> przestrzeni nazw. Użyj <xref:System.Transactions.TransactionScope> obiektu, aby uczestniczyć w transakcji, która jest automatycznie zarządzana.

Projekty nie są tworzone z odwołaniem do zestawu *System. Transactions* , więc musisz ręcznie dodać odwołanie do projektów, które używają transakcji.

Najprostszym sposobem implementacji transakcji jest utworzenie wystąpienia <xref:System.Transactions.TransactionScope> obiektu w `using` instrukcji. (Aby uzyskać więcej informacji, zobacz [using instrukcji](/dotnet/visual-basic/language-reference/statements/using-statement)and [using](/dotnet/csharp/language-reference/keywords/using-statement).) Kod, który jest uruchamiany w ramach `using` instrukcji, uczestniczy w transakcji.

Aby zatwierdzić transakcję, wywołaj <xref:System.Transactions.TransactionScope.Complete%2A> metodę jako ostatnią instrukcję w bloku using.

Aby wycofać transakcję, Zgłoś wyjątek przed wywołaniem <xref:System.Transactions.TransactionScope.Complete%2A> metody.

## <a name="to-add-a-reference-to-the-systemtransactionsdll"></a>Aby dodać odwołanie do System.Transactions.dll

1. W menu **projekt** wybierz polecenie **Dodaj odwołanie**.

2. Na karcie **.NET** (**SQL Server** karcie Projekty SQL Server) wybierz pozycję **System. Transactions**, a następnie wybierz przycisk **OK**.

     Odwołanie do *System.Transactions.dll* jest dodawane do projektu.

## <a name="to-save-data-in-a-transaction"></a>Aby zapisać dane w transakcji

- Dodaj kod, aby zapisać dane w instrukcji using zawierającej transakcję. Poniższy kod pokazuje, jak utworzyć i utworzyć wystąpienie <xref:System.Transactions.TransactionScope> obiektu w instrukcji using:

     [!code-vb[VbRaddataSaving#11](../data-tools/codesnippet/VisualBasic/save-data-by-using-a-transaction_1.vb)]
     [!code-csharp[VbRaddataSaving#11](../data-tools/codesnippet/CSharp/save-data-by-using-a-transaction_1.cs)]

## <a name="see-also"></a>Zobacz też

- [Zapisywanie danych z powrotem w bazie danych](../data-tools/save-data-back-to-the-database.md)
- [Przewodnik: zapisywanie danych w transakcji](../data-tools/save-data-in-a-transaction.md)
