---
title: Ustawianie informacji o konfiguracji dla rozwiązań pakietu Office
ms.date: 02/02/2017
ms.topic: conceptual
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
ms.openlocfilehash: c477068b3aee3325acae0887e11da908d6c33a85
ms.sourcegitcommit: 7eb2fb21805d92f085126f3a820ac274f2216b4e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/22/2019
ms.locfileid: "67328899"
---
# <a name="how-to-set-up-configuration-information-for-an-office-solution"></a>Instrukcje: Ustawianie informacji o konfiguracji dla rozwiązań pakietu Office
  Pliki konfiguracji można użyć do konfigurowania ustawień, które są specyficzne dla rozwiązania pakietu Office. Można określić ustawienia, takie jak zasady tworzenia powiązań zestawów, obiekty usług zdalnych, debugowania i ustawienia śledzenia.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

### <a name="to-add-a-configuration-file-to-your-office-project"></a>Aby dodać plik konfiguracji do projektu pakietu Office

1. Na **projektu** menu, kliknij przycisk **Dodaj nowy element**.

2. W **kategorie** okienku kliknij **ogólne**.

3. W **szablony** okienku wybierz **pliku konfiguracji aplikacji**.

4. W **nazwa** wpisz taką samą nazwę jak zestawu oraz rozszerzenie *.config*. Na przykład plik konfiguracji dla zestawu projektu programu Excel o nazwie *ExcelWorkbook1.dll* będą miały postać *ExcelWorkbook1.dll.config*.

5. Kliknij przycisk **Dodaj**.

6. Utwórz plik konfiguracji zgodnie z schemat pliku konfiguracji aplikacji. Aby uzyskać więcej informacji, zobacz [schemat pliku konfiguracji dla programu .NET Framework](/dotnet/framework/configure-apps/file-schema/index).

   Nie istnieją żadne specjalne uwagi dotyczące za pomocą plików konfiguracji przy użyciu projektów pakietu Office.

## <a name="see-also"></a>Zobacz także
- [Schemat pliku konfiguracji dla programu .NET Framework](/dotnet/framework/configure-apps/file-schema/index)
- [Projektowanie i tworzenie rozwiązań pakietu Office](../vsto/designing-and-creating-office-solutions.md)
- [Wdrażanie rozwiązania do pakietu Office](../vsto/deploying-an-office-solution.md)
