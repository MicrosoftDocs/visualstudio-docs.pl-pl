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
ms.openlocfilehash: c22a0cc9b0b9d37a4d725aa8ce494646e7779f0f
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2021
ms.locfileid: "106216075"
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

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form2.vb" id="Snippet11":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form2.cs" id="Snippet11":::

## <a name="see-also"></a>Zobacz też

- [Zapisywanie danych z powrotem w bazie danych](../data-tools/save-data-back-to-the-database.md)
- [Przewodnik: zapisywanie danych w transakcji](../data-tools/save-data-in-a-transaction.md)
