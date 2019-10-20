---
title: Wybrano obiekt bazy danych z nieobsługiwanego dostawcy bazy danych | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: c0f1298e-31aa-471e-ae19-1bafffd2ae40
caps.latest.revision: 8
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 05a4407eba52ec3940b70ffab220ef354af90e9d
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72657789"
---
# <a name="you-have-selected-a-database-object-from-an-unsupported-database-provider"></a>Wybrano obiekt bazy danych od nieobsługiwanego dostawcy bazy danych
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

@No__t_0 ([!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]) obsługuje tylko .NET Framework Dostawca danych dla SQL Server (<xref:System.Data.SqlClient>). Mimo że można kliknąć przycisk **OK** i kontynuować pracę z obiektami z nieobsługiwanych dostawców baz danych, może wystąpić nieoczekiwane zachowanie w czasie wykonywania.

> [!NOTE]
> Obsługiwane są tylko połączenia danych używające Dostawca danych .NET Framework dla SQL Server.

### <a name="to-correct-this-error"></a>Aby poprawić ten błąd

- Kliknij przycisk **OK** , aby kontynuować projektowanie klas jednostek, które są mapowane na połączenie, które korzysta z nieobsługiwanego dostawcy bazy danych. W przypadku korzystania z nieobsługiwanych dostawców baz danych może wystąpić nieoczekiwane zachowanie.

     —lub—

- Kliknij przycisk **Anuluj**.

     Akcja jest zatrzymana. Utwórz lub Użyj połączenia danych, które używa dostawcy .NET Framework dla SQL Server.

## <a name="see-also"></a>Zobacz też
 [LINQ to SQL narzędzia w programie Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) [LINQ to SQL](https://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655) [.NET Framework dostawcach danych](https://msdn.microsoft.com/library/03a9fc62-2d24-491a-9fe6-d6bdb6dcb131)