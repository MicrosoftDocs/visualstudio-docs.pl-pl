---
title: Docelowa aplikacja pakietu Office przy użyciu podstawowych zestawów międzyoperacyjnych
ms.date: 02/02/2017
ms.topic: how-to
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
ms.openlocfilehash: 60e351a15af4994d2bf64a800e3019501cf0571d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85545772"
---
# <a name="how-to-target-office-applications-through-primary-interop-assemblies"></a>Jak: docelowa aplikacja pakietu Office przy użyciu podstawowych zestawów międzyoperacyjnych
  Podczas tworzenia nowego projektu pakietu Office Program Visual Studio automatycznie dodaje odwołania do Microsoft Office podstawowych zestawów międzyoperacyjnych (zestawów PIA), które są wymagane do skompilowania projektu. Należy dodać odwołania do innych zestawów PIA w następujących scenariuszach:

- Chcesz używać funkcji innych aplikacji Microsoft Office w projekcie. Na przykład możesz chcieć użyć funkcji programu Microsoft Office Excel w projekcie dla Microsoft Office Word.

- Chcesz zautomatyzować Microsoft Office aplikacje, które nie mają dedykowanych projektów w programie Visual Studio, takich jak Microsoft Office Access.

  [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="to-add-a-reference-to-a-primary-interop-assembly"></a>Aby dodać odwołanie do podstawowego zestawu międzyoperacyjnego

1. Otwórz projekt pakietu Office i wybierz nazwę projektu w **Eksplorator rozwiązań**.

2. W menu **projekt** kliknij polecenie **Dodaj odwołanie**.

3. Na karcie **Struktura** wybierz odpowiedni Pia na liście **Nazwa składnika** . Aby uzyskać więcej informacji na temat dostępnych Microsoft Office podstawowych zestawów międzyoperacyjnych, zobacz [podstawowe zestawy międzyoperacyjności pakietu Office](../vsto/office-primary-interop-assemblies.md).

     Jeśli projekt jest przeznaczony dla [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub później, właściwość **Osadź typy** współdziałania dla odwołania do zestawu jest domyślnie ustawiona na **true** . Korzystając z tego ustawienia, Twoje rozwiązanie nie wymaga ustawienia PIA na komputerach użytkowników końcowych. Aby uzyskać więcej informacji, zobacz [projektowanie i tworzenie rozwiązań pakietu Office](../vsto/designing-and-creating-office-solutions.md).

    > [!NOTE]
    > W projektach pakietu Office zawsze Dodaj odwołania do pakietu Office zestawów Pia przy użyciu karty **.NET** okna dialogowego **Dodaj odwołanie** , a nie karty **com** . Aby uzyskać więcej informacji, zobacz [zestawy podstawowych międzyoperacyjnych pakietu Office](../vsto/office-primary-interop-assemblies.md).

4. Kliknij przycisk **OK**.

     Nazwa zestawu pojawia się w folderze **References** elementu **Eksplorator rozwiązań**.

## <a name="see-also"></a>Zobacz też
- [Podstawowe zestawy międzyoperacyjności pakietu Office](../vsto/office-primary-interop-assemblies.md)
- [Pisanie kodu w rozwiązaniach pakietu Office](../vsto/writing-code-in-office-solutions.md)
- [Opracowywanie rozwiązań pakietu Office](../vsto/developing-office-solutions.md)
- [Instrukcje: Instalowanie podstawowych zestawów międzyoperacyjnych pakietu Office](../vsto/how-to-install-office-primary-interop-assemblies.md)
