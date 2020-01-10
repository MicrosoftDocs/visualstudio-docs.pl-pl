---
title: Używanie starszej wersji projektanta działań | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- activities, configuring
- custom activities
- Activity Designer
- child activities, adding
- activities, adding child
- activities, creating custom
ms.assetid: 2fea8a05-6e58-423d-94bf-a822b15ffb80
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: cd8d18d95fabd858354c625d2c9b32459efc7193
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/10/2020
ms.locfileid: "75846151"
---
# <a name="using-the-legacy-activity-designer"></a>Używanie starszej wersji projektanta działań
W tym temacie opisano, jak używać projektanta działań w starszej [!INCLUDE[wfd1](../includes/wfd1-md.md)]. Użyj starszego projektanta podczas określania [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] lub [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].

 Projektant działań umożliwia tworzenie własnych działań niestandardowych.

## <a name="creating-a-custom-activity"></a>Tworzenie działania niestandardowego
 Wykonaj następujące kroki, aby utworzyć niestandardowe działanie za pomocą projektanta działań:

1. W menu **projekt** kliknij polecenie **Dodaj działanie**.

2. Wybierz szablon **działanie** lub **działanie (z separacją kodu)** .

   1. Użyj szablonu **działania** , aby utworzyć działanie z definicją działania i kodem użytkownika w tym samym pliku kodu.

   2. Za pomocą szablonu **działanie (z separacją kodu)** można utworzyć działanie z definicją działania wyrażoną jako znacznik przepływu pracy i kod użytkownika w osobnym pliku kodu.

3. Wpisz nazwę działania lub Zachowaj nazwę domyślną, a następnie kliknij przycisk **Dodaj**.

   Możesz również utworzyć zestaw działań niestandardowych, tworząc nowy projekt typu **Biblioteka działań przepływu pracy**. Aby uzyskać więcej informacji na temat tego typu projektu, zobacz [How to: Create a Workflow Activity Library (starsza wersja)](../workflow-designer/how-to-create-a-workflow-activity-library-legacy.md).

## <a name="configuring-an-activity"></a>Konfigurowanie działania
 Gdy Projektant działań jest aktywny, można użyć przeglądarki właściwości, aby skonfigurować właściwości wymienione w poniższej tabeli.

|Właściwość|Komentarze|
|--------------|--------------|
|**Nazwa**|Nazwa działania.|
|**Klasa bazowa**|Klasa bazowa, z której pochodzi działanie. Domyślną klasą bazową jest [SequenceActivity](https://msdn2.microsoft.com/library/system.workflow.activities.sequenceactivity.aspx). W oknie **Właściwości** kliknij wielokropek **klasy bazowej** **[...]** , aby wybrać inną klasę bazową w oknie [dialogowym Przeglądaj i wybierz typ platformy .NET (starsza wersja)](../workflow-designer/browse-and-select-a-dotnet-type-dialog-box-legacy.md).|
|**Opis**|Opis działania zdefiniowany przez użytkownika.|
|**Włączono**|Domyślnie Ustaw **wartość true** , aby włączyć wykonywanie i sprawdzanie poprawności działania. Ustaw **wartość false** , aby wyłączyć wykonywanie i sprawdzanie poprawności działania. Informacje o wykonywaniu i walidacji działania znajdują się w temacie [opracowywanie działań przepływu pracy](https://msdn2.microsoft.com/library/ms734413.aspx).|

## <a name="adding-child-activities"></a>Dodawanie działań podrzędnych
 Możesz przeciągać działania podrzędne z przybornika do projektowanego działania. Następnie można skonfigurować każde działanie podrzędne przy użyciu przeglądarki właściwości.

## <a name="see-also"></a>Zobacz też
 [Opracowywanie działań przepływu pracy](https://msdn2.microsoft.com/library/ms734413.aspx) [Tworzenie działań niestandardowych](https://msdn2.microsoft.com/library/bb675228.aspx) [starsze działania przepływów pracy](../workflow-designer/legacy-workflow-activities.md) — [przykłady czynności](https://msdn2.microsoft.com/library/bb472471.aspx) [: Tworzenie biblioteki działań przepływu pracy (starsza wersja)](../workflow-designer/how-to-create-a-workflow-activity-library-legacy.md) [przy użyciu starszej wersji Projektant przepływu pracy](../workflow-designer/using-the-legacy-workflow-designer.md)
