---
title: Obiekt z nieobsługiwanego dostawcy
description: Wybrano obiekt bazy danych od nieobsługiwanego dostawcy bazy danych
ms.date: 11/04/2016
ms.topic: error-reference
ms.assetid: c0f1298e-31aa-471e-ae19-1bafffd2ae40
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: a4867ab2e7d8f269961c7d1a783a3b31d70da05d
ms.sourcegitcommit: 2a201c93ed526b0f7e5848657500f1111b08ac2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2020
ms.locfileid: "89743168"
---
# <a name="you-have-selected-a-database-object-from-an-unsupported-database-provider"></a>Wybrano obiekt bazy danych od nieobsługiwanego dostawcy bazy danych

**Projektant O/R** obsługuje tylko .NET Framework Dostawca danych dla SQL Server ( <xref:System.Data.SqlClient> ). Mimo że można kliknąć przycisk **OK** i kontynuować pracę z obiektami z nieobsługiwanych dostawców baz danych, może wystąpić nieoczekiwane zachowanie w czasie wykonywania.

> [!NOTE]
> Obsługiwane są tylko połączenia danych używające Dostawca danych .NET Framework dla SQL Server.

## <a name="options"></a>Opcje

- Kliknij przycisk **OK** , aby kontynuować projektowanie klas jednostek, które są mapowane na połączenie, które korzysta z nieobsługiwanego dostawcy bazy danych. W przypadku korzystania z nieobsługiwanych dostawców baz danych może wystąpić nieoczekiwane zachowanie.

- Kliknij przycisk **Anuluj** , aby zatrzymać akcję. Utwórz lub użyj innego połączenia danych, które używa dostawcy .NET Framework dla SQL Server.

## <a name="see-also"></a>Zobacz także

- [Narzędzia LINQ to SQL w programie Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
