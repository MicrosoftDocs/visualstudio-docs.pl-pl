---
title: 'Instrukcje: korzystanie z wizualizatora | Microsoft Docs'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "64778379"
---
# <a name="how-to-use-a-visualizer"></a>Porady: korzystanie z wizualizatora
Możesz użyć wizualizatora, aby wyświetlić zawartość zmiennej lub obiektu w sposób zrozumiały dla typu danych. Wizualizatorów można używać ze **wskazówkami**do danych, oknem **czujki** , oknem **autostarts** lub oknem **lokalnym** .  
  
 Wizualizatory nie są obsługiwane w środowisku kompaktowym.  
  
> [!NOTE]
> W aplikacjach ze **sklepu** obsługiwane są tylko Wizualizatory tekstu standardowego, HTML, XML i JSON. Wizualizacje niestandardowe (utworzone przez użytkownika) nie są obsługiwane.  
  
### <a name="to-open-a-visualizer"></a>Aby otworzyć wizualizator  
  
1. Kliknij ikonę lupy, która pojawia się obok nazwy **zmiennej w obszarze** **datawatchs** , w oknie czujki lub **w oknie elementy**AutoWatch, **lokalne**lub **szybkie czujka** .  
  
     Zostanie wyświetlona lista wizualizatorów.  
  
2. Kliknij wizualizator, którego chcesz użyć.  
  
### <a name="to-use-a-visualizer-for-managed-code-during-remote-debugging"></a>Aby użyć wizualizatora dla kodu zarządzanego podczas debugowania zdalnego  
  
- Przed rozpoczęciem sesji debugowania Skopiuj plik DLL wizualizatora na komputer zdalny.  
  
     Ścieżka do biblioteki DLL musi być taka sama na komputerach zdalnych i lokalnych. Ta ścieżka może być jedną z następujących lokalizacji:  
  
     *Ścieżka instalacji programu Visual Studio*`\Common7\Packages\Debugger\Visualizers`  
  
     -lub-  
  
     `My Documents\Visual Studio 2010\Visualizers`*Wersja programu Visual Studio*`\Visualizers`  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie wizualizacji niestandardowych](../debugger/create-custom-visualizers-of-data.md)   
 [Instrukcje: Instalowanie wizualizatora](../debugger/how-to-install-a-visualizer.md)   
 [Instrukcje: pisanie wizualizatora](../debugger/how-to-write-a-visualizer.md)   
 [Wyświetlanie wartości danych w etykietkach danych](../debugger/view-data-values-in-data-tips-in-the-code-editor.md)