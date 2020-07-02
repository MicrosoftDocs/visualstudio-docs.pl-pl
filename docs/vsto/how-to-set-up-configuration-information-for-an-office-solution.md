---
title: Konfigurowanie informacji o konfiguracji dla rozwiązania pakietu Office
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- solutions [Office development in Visual Studio], configuration files
- configuration files [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 8a0868019247e20b9154690469d4c291f1f8e0d6
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/30/2020
ms.locfileid: "85545811"
---
# <a name="how-to-set-up-configuration-information-for-an-office-solution"></a>Instrukcje: Konfigurowanie informacji o konfiguracji dla rozwiązania pakietu Office
  Za pomocą plików konfiguracji można skonfigurować ustawienia specyficzne dla rozwiązań pakietu Office. Można określić ustawienia, takie jak zasady powiązań zestawu, obiekty zdalne, debugowanie i ustawienia śledzenia.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

### <a name="to-add-a-configuration-file-to-your-office-project"></a>Aby dodać plik konfiguracji do projektu pakietu Office

1. W menu **projekt** kliknij polecenie **Dodaj nowy element**.

2. W okienku **Kategorie** kliknij pozycję **Ogólne**.

3. W okienku **Szablony** wybierz pozycję **plik konfiguracji aplikacji**.

4. W polu **Nazwa** wpisz taką samą nazwę, jak zestaw i rozszerzenie *. config*. Na przykład plik konfiguracyjny zestawu projektu programu Excel o nazwie *ExcelWorkbook1.dll* zostałby nazwany *ExcelWorkbook1.dll.config*.

5. Kliknij pozycję **Dodaj**.

6. Utwórz plik konfiguracji zgodnie ze schematem pliku konfiguracji aplikacji. Aby uzyskać więcej informacji, zobacz [Schemat pliku konfiguracji dla .NET Framework](/dotnet/framework/configure-apps/file-schema/index).

   Nie ma specjalnych zagadnień dotyczących używania plików konfiguracji z projektami pakietu Office.

## <a name="see-also"></a>Zobacz także
- [Schemat pliku konfiguracji dla .NET Framework](/dotnet/framework/configure-apps/file-schema/index)
- [Projektowanie i tworzenie rozwiązań pakietu Office](../vsto/designing-and-creating-office-solutions.md)
- [Wdróż rozwiązanie pakietu Office](../vsto/deploying-an-office-solution.md)
