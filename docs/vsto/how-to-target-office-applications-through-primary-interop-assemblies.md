---
title: Kierowanie aplikacji pakietu Office przy użyciu podstawowych zestawów międzyoperacyjnych
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- assemblies [Office development in Visual Studio], PIA references
- primary interop assemblies [Office development in Visual Studio], adding references to
- Office primary interop assemblies in Visual Studio, adding references to
- Office applications [Office development in Visual Studio], automating
- application development [Office development in Visual Studio], automating
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: c6e92b3b4dd46885de7f30f5364d30f39b5c2bd7
ms.sourcegitcommit: 7eb2fb21805d92f085126f3a820ac274f2216b4e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/22/2019
ms.locfileid: "67328879"
---
# <a name="how-to-target-office-applications-through-primary-interop-assemblies"></a>Instrukcje: Konfigurowanie pod kątem aplikacji pakietu Office przy użyciu podstawowych zestawów międzyoperacyjnych
  Podczas tworzenia nowego projektu pakietu Office, Visual Studio automatycznie dodaje odwołania do programu Microsoft Office podstawowe zestawy międzyoperacyjne (PIA), które są wymagane do kompilowania projektu. Należy dodać odwołania do innych zestawów PIA w następujących scenariuszach:

- Chcesz korzystać z funkcji innych aplikacji pakietu Microsoft Office w projekcie. Na przykład można używać funkcji programu Microsoft Office Excel w projekcie dla programu Microsoft Office Word.

- Chcesz zautomatyzować aplikacji Microsoft Office, które nie mają dedykowanych projektów w programie Visual Studio, takich jak Microsoft Office Access.

  [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="to-add-a-reference-to-a-primary-interop-assembly"></a>Aby dodać odwołanie do podstawowego zestawu międzyoperacyjnego

1. Otwórz projekt pakietu Office i wybierz nazwę projektu w **Eksploratora rozwiązań**.

2. Na **projektu** menu, kliknij przycisk **Dodaj odwołanie**.

3. Na **Framework** , a następnie wybierz PIA w **nazwa składnika** listy. Aby uzyskać więcej informacji na temat dostępnych podstawowych zestawów międzyoperacyjnych programu Microsoft Office, zobacz [podstawowe zestawy międzyoperacyjne pakietu Office](../vsto/office-primary-interop-assemblies.md).

     Jeśli projekt jest ukierunkowany [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub nowszym, **Osadź typy współdziałania** dla odwołania do zestawu jest właściwością **True** domyślnie. Za pomocą tego ustawienia, rozwiązanie nie wymaga PIA na komputerach użytkowników końcowych. Aby uzyskać więcej informacji, zobacz [projektowania i tworzenia rozwiązań dla pakietu Office](../vsto/designing-and-creating-office-solutions.md).

    > [!NOTE]
    > W projektach pakietu Office, zawsze dodać odwołania do zestawów PIA pakietu Office za pomocą **.NET** karcie **Dodaj odwołanie** okna dialogowego, a nie od **COM** kartę. Aby uzyskać więcej informacji, zobacz [podstawowe zestawy międzyoperacyjne pakietu Office](../vsto/office-primary-interop-assemblies.md).

4. Kliknij przycisk **OK**.

     Nazwa zestawu, który pojawia się w **odwołania** folderu **Eksploratora rozwiązań**.

## <a name="see-also"></a>Zobacz także
- [Podstawowe zestawy międzyoperacyjne pakietu Office](../vsto/office-primary-interop-assemblies.md)
- [Pisanie kodu w rozwiązaniach pakietu Office](../vsto/writing-code-in-office-solutions.md)
- [Opracowywania rozwiązań pakietu Office](../vsto/developing-office-solutions.md)
- [Instrukcje: Instalowanie podstawowych zestawów międzyoperacyjnych pakietu Office](../vsto/how-to-install-office-primary-interop-assemblies.md)
