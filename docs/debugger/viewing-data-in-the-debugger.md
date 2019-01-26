---
title: Tworzenie niestandardowych widoków danych w debugerze | Dokumentacja firmy Microsoft
ms.date: 01/09/2019
ms.topic: conceptual
f1_keywords:
- vs.debug
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- debugging [Visual Studio], inspecting programs
- debugger, viewing data
ms.assetid: 13e1105f-f987-402e-9108-ec6ac12be042
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b00eb9127247c98324b64a998ea8c13cb47e074d
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "55030486"
---
# <a name="create-custom-views-of-data-in-the-visual-studio-debugger-c-visual-basic-c"></a>Tworzenie niestandardowych widoków danych w debugerze programu Visual Studio (C#, Visual Basic, C++)

[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Debugger udostępnia wiele narzędzi do inspekcji i modyfikacji stanu programu. Większość tych narzędzi działa tylko w trybie przerwania.

## <a name="create-custom-views-of-data-in-variable-windows-and-datatips"></a>Tworzenie niestandardowych widoków danych w oknach zmiennych i etykietki danych

 Wiele [okna debugera](../debugger/debugger-windows.md), takich jak **Autos** i **Obejrzyj** systemu windows, pozwalają na sprawdzanie zmiennych. Można dostosować sposób natywnych typów, zarządzanych obiektów i własne typy nie są wyświetlane w oknach zmiennych debugera, a w [DataTips](../debugger/view-data-values-in-data-tips-in-the-code-editor.md). Aby uzyskać więcej informacji, zobacz [Tworzenie niestandardowych widoków obiektów macierzystych](../debugger/create-custom-views-of-native-objects.md) i [Tworzenie niestandardowych widoków obiektów](../debugger/create-custom-views-of-dot-managed-objects.md).
  
## <a name="create-custom-visualizers"></a>Tworzenie niestandardowych wizualizatorów

 Wizualizatory umożliwiają wyświetlanie zawartości zmiennej lub obiektu w znaczący sposób. W debugerze programu Visual Studio wizualizatora odnosi się do innego systemu windows, które można otworzyć za pomocą ikonę lupy ![VisualizerIcon](../debugger/media/dbg-tips-visualizer-icon.png "ikonę Wizualizator") ikony. Na przykład wizualizatora HTML pokazuje, jak byłby interpretowany i wyświetlany w przeglądarce ciągu HTML. Dostęp wizualizatorów można uzyskać poprzez DataTips, **Obejrzyj** oknie **Autos** oknie i **lokalne** okna. **QuickWatch** okno dialogowe udostępnia również wizualizatora. Aby uzyskać więcej informacji, zobacz [Tworzenie niestandardowych wizualizatorów](../debugger/create-custom-visualizers-of-data.md).
  
## <a name="see-also"></a>Zobacz także

 [Pierwsze spojrzenie na debugera](../debugger/debugger-feature-tour.md) [okna polecenia](../ide/reference/command-window.md)   
 [Zabezpieczenia debugera](../debugger/debugger-security.md)