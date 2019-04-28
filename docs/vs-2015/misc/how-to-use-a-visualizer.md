---
title: 'Instrukcje: Korzystanie z wizualizatora | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
f1_keywords:
- vs.debug.dataviewer
- vs.debug.stringviewer
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- debugger, visualizers
- visualizers, about visualizers
ms.assetid: d2611385-0134-4387-8c5a-979fe625a462
caps.latest.revision: 37
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 0f981b76d471658fe82e874901ad784a17841891
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63446434"
---
# <a name="how-to-use-a-visualizer"></a>Instrukcje: Korzystanie z wizualizatora
Korzystanie z wizualizatora, aby wyświetlić zawartość zmiennej lub obiektu w sposób zrozumiały dla typu danych. Można użyć wizualizatorów z **DataTips**, **Obejrzyj** oknie **automatyczne** oknie lub **zmiennych lokalnych** okna.  
  
 Wizualizatory nie są obsługiwane w Compact Framework.  
  
> [!NOTE]
> W **Store** aplikacji, tylko standardowy tekst, HTML, XML i JSON wizualizatory są obsługiwane. Wizualizatory niestandardowe (utworzone przez użytkownika) nie są obsługiwane.  
  
### <a name="to-open-a-visualizer"></a>Aby otworzyć wizualizatora  
  
1. Kliknij ikonę lupy, która pojawia się obok nazwy zmiennej w **DataTips**, **Obejrzyj** oknie lub w **Autos**, **lokalne**, lub **Quick Watch** okna.  
  
     Zostanie wyświetlona lista wizualizatorów.  
  
2. Kliknij pozycję Wizualizator, którego chcesz użyć.  
  
### <a name="to-use-a-visualizer-for-managed-code-during-remote-debugging"></a>Aby korzystanie z wizualizatora dla zarządzanego kodu podczas debugowania zdalnego  
  
- Skopiuj Wizualizator biblioteki DLL do komputera zdalnego, przed rozpoczęciem sesji debugowania.  
  
     Ścieżka do biblioteki DLL musi być taka sama, zarówno w przypadku zdalnego, jak i komputerów lokalnych. Ta ścieżka może być jedną z następujących lokalizacji:  
  
     *Ścieżka instalacji usługi Visual Studio* `\Common7\Packages\Debugger\Visualizers`  
  
     —lub—  
  
     `My Documents\Visual Studio 2010\Visualizers` *Visual Studio Version* `\Visualizers`  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie niestandardowych Wizualizatorów](../debugger/create-custom-visualizers-of-data.md)   
 [Instrukcje: Instalacja programu Visualizer](../debugger/how-to-install-a-visualizer.md)   
 [Instrukcje: Pisanie wizualizatora](../debugger/how-to-write-a-visualizer.md)   
 [Wyświetlanie wartości danych w etykietkach danych](../debugger/view-data-values-in-data-tips-in-the-code-editor.md)