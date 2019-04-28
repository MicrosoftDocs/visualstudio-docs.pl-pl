---
title: Zapisywanie danych przy użyciu transakcji | Dokumentacja firmy Microsoft
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 260396123f806e7c37b91ff4aca643a05853676f
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63425088"
---
# <a name="save-data-by-using-a-transaction"></a>Zapisywanie danych przy użyciu transakcji
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Zapisywanie danych w ramach transakcji przy użyciu <xref:System.Transactions> przestrzeni nazw. Użyj <xref:System.Transactions.TransactionScope> obiekt, aby uczestniczyć w transakcji, które są zarządzane automatycznie dla Ciebie.  
  
 Projekty nie są tworzone za pomocą odwołania do zestawu System.Transactions, więc trzeba ręcznie dodać odwołania do projektów, które korzystają z transakcji.  
  
> [!NOTE]
> <xref:System.Transactions> Przestrzeni nazw jest obsługiwana w systemie Windows 2000 lub nowszym.  
  
 Najłatwiejszym sposobem realizowania transakcji jest utworzenie wystąpienia <xref:System.Transactions.TransactionScope> obiektu `using` instrukcji. (Aby uzyskać więcej informacji, zobacz [instrukcji Using](http://msdn.microsoft.com/library/665d1580-dd54-4e96-a9a9-6be2a68948f1), i [za pomocą instrukcji](http://msdn.microsoft.com/library/afc355e6-f0b9-4240-94dd-0d93f17d9fc3).) Kod, który jest uruchamiany w ramach `using` instrukcji bierze udział w transakcji.  
  
 Aby zatwierdzić transakcji, należy wywołać <xref:System.Transactions.TransactionScope.Complete%2A> block metodę jako ostatnią instrukcję w przy użyciu.  
  
 Aby wycofać transakcji zgłoszenie wyjątku przed wywołaniem <xref:System.Transactions.TransactionScope.Complete%2A> metody.  
  
 Aby uzyskać więcej informacji, zobacz [zapisywanie danych w ramach transakcji](../data-tools/save-data-in-a-transaction.md).  
  
### <a name="to-add-a-reference-to-the-systemtransactions-dll"></a>Aby dodać odwołanie do biblioteki dll System.Transactions  
  
1. Na **projektu** menu, wybierz opcję **Dodaj odwołanie**.  
  
2. Na **.NET** kartę (**programu SQL Server** kartę dla projektów programu SQL Server), wybierz opcję **System.Transactions**, a następnie wybierz pozycję **OK**.  
  
     Odwołanie do System.Transactions.dll zostanie dodany do projektu.  
  
### <a name="to-save-data-in-a-transaction"></a>Aby zapisać dane w ramach transakcji  
  
- Dodaj kod, aby zapisać dane w obrębie za pomocą instrukcji, która zawiera transakcji. Poniższy kod przedstawia sposób tworzenia i utworzyć wystąpienie <xref:System.Transactions.TransactionScope> obiektu w za pomocą instrukcji:  
  
     [!code-csharp[VbRaddataSaving#11](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form2.cs#11)]
     [!code-vb[VbRaddataSaving#11](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form2.vb#11)]  
  
## <a name="see-also"></a>Zobacz też  
 [Zapisywanie danych z powrotem w bazie danych](../data-tools/save-data-back-to-the-database.md)
