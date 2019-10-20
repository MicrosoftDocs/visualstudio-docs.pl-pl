---
title: Zapisywanie danych przy użyciu transakcji | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- saving data, using transactions
- System.Transactions namespace
- transactions, saving data
- data [Visual Studio], saving
ms.assetid: 8b835e8f-34a3-413d-9bb5-ebaeb87f1198
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 85f3584073523e748168faf569aa918ba912fbf8
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72652834"
---
# <a name="save-data-by-using-a-transaction"></a>Zapisywanie danych przy użyciu transakcji
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Dane są zapisywane w transakcji przy użyciu przestrzeni nazw <xref:System.Transactions>. Użyj obiektu <xref:System.Transactions.TransactionScope>, aby wziąć udział w transakcji, która jest automatycznie zarządzana.

 Projekty nie są tworzone z odwołaniem do zestawu System. Transactions, więc musisz ręcznie dodać odwołanie do projektów, które używają transakcji.

> [!NOTE]
> Przestrzeń nazw <xref:System.Transactions> jest obsługiwana w systemie Windows 2000 lub nowszym.

 Najprostszym sposobem implementacji transakcji jest utworzenie wystąpienia obiektu <xref:System.Transactions.TransactionScope> w instrukcji `using`. (Aby uzyskać więcej informacji, zobacz [using instrukcji](https://msdn.microsoft.com/library/665d1580-dd54-4e96-a9a9-6be2a68948f1)and [using](https://msdn.microsoft.com/library/afc355e6-f0b9-4240-94dd-0d93f17d9fc3).) Kod, który jest uruchamiany w instrukcji `using` uczestniczy w transakcji.

 Aby zatwierdzić transakcję, wywołaj metodę <xref:System.Transactions.TransactionScope.Complete%2A> jako ostatnią instrukcję w bloku using.

 Aby wycofać transakcję, Zgłoś wyjątek przed wywołaniem metody <xref:System.Transactions.TransactionScope.Complete%2A>.

 Aby uzyskać więcej informacji, zobacz [Zapisywanie danych w transakcji](../data-tools/save-data-in-a-transaction.md).

### <a name="to-add-a-reference-to-the-systemtransactions-dll"></a>Aby dodać odwołanie do biblioteki DLL system. Transactions

1. W menu **projekt** wybierz polecenie **Dodaj odwołanie**.

2. Na karcie **.NET** (**SQL Server** karcie Projekty SQL Server) wybierz pozycję **System. Transactions**, a następnie wybierz przycisk **OK**.

     Odwołanie do System. Transactions. dll jest dodawane do projektu.

### <a name="to-save-data-in-a-transaction"></a>Aby zapisać dane w transakcji

- Dodaj kod, aby zapisać dane w instrukcji using zawierającej transakcję. Poniższy kod pokazuje, jak utworzyć i utworzyć wystąpienie obiektu <xref:System.Transactions.TransactionScope> w instrukcji using:

     [!code-csharp[VbRaddataSaving#11](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form2.cs#11)]
     [!code-vb[VbRaddataSaving#11](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form2.vb#11)]

## <a name="see-also"></a>Zobacz też
 [Zapisywanie danych z powrotem w bazie danych](../data-tools/save-data-back-to-the-database.md)
