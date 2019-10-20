---
title: Wybrano obiekt bazy danych od nieobsługiwanego dostawcy bazy danych
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: c0f1298e-31aa-471e-ae19-1bafffd2ae40
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: b1dd14c428b90b87e665aa41681b5a9e68eb00e5
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72648021"
---
# <a name="you-have-selected-a-database-object-from-an-unsupported-database-provider"></a>Wybrano obiekt bazy danych od nieobsługiwanego dostawcy bazy danych

**Projektant O/R** obsługuje tylko .NET Framework Dostawca danych dla SQL Server (<xref:System.Data.SqlClient>). Mimo że można kliknąć przycisk **OK** i kontynuować pracę z obiektami z nieobsługiwanych dostawców baz danych, może wystąpić nieoczekiwane zachowanie w czasie wykonywania.

> [!NOTE]
> Obsługiwane są tylko połączenia danych używające Dostawca danych .NET Framework dla SQL Server.

## <a name="options"></a>Opcje

- Kliknij przycisk **OK** , aby kontynuować projektowanie klas jednostek, które są mapowane na połączenie, które korzysta z nieobsługiwanego dostawcy bazy danych. W przypadku korzystania z nieobsługiwanych dostawców baz danych może wystąpić nieoczekiwane zachowanie.

- Kliknij przycisk **Anuluj** , aby zatrzymać akcję. Utwórz lub użyj innego połączenia danych, które używa dostawcy .NET Framework dla SQL Server.

## <a name="see-also"></a>Zobacz także

- [Narzędzia LINQ to SQL w programie Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)