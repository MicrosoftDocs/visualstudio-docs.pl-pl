---
title: 'Instrukcje: Debugowanie w trybie mieszanym | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
- C++
helpviewer_keywords:
- debugging DLLs
- debugging [Visual Studio], mixed-mode
- mixed-mode debugging
ms.assetid: 2859067d-7fcc-46b0-a4df-8c2101500977
caps.latest.revision: 32
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: bb1bcaf6eac3d8ad671a8b610c9b45821a93e7b4
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63438448"
---
# <a name="how-to-debug-in-mixed-mode"></a>Instrukcje: Debugowanie w trybie mieszanym
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W poniższych procedurach opisano sposób debugowania kodu zarządzanego i natywnego, tzw. debugowanie w trybie mieszanym. Istnieją dwa scenariusze, aby to zrobić, w zależności od tego, czy biblioteka DLL lub w aplikacji są zapisywane w kodzie natywnym:  
  
- Aplikacja wywołująca, która wywołuje bibliotekę DLL są zapisywane w kodzie natywnym. W tym przypadku jest zarządzana biblioteka DLL i debugery zarówno zarządzanego i natywnego musi być włączona debugować oba. Można to sprawdzić  **\<Projekt > strony właściwości** okno dialogowe. Jak to zrobić, zależy od tego, czy rozpoczynasz debugowanie z projektu DLL lub wywoływania projektu aplikacji.  
  
- Aplikacja wywołująca, która wywołuje bibliotekę DLL są zapisywane w kodzie zarządzanym i biblioteki DLL są zapisywane w kodzie natywnym.  
  
> [!NOTE]
> Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić swoje ustawienia, wybierz opcję **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień środowiska deweloperskiego, w programie Visual Studio](http://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-enable-mixed-mode-debugging"></a>Aby włączyć debugowanie w trybie mieszanym  
  
1. W **Eksploratora rozwiązań**, wybierz projekt.  
  
2. Na **widoku** menu, kliknij przycisk **stron właściwości**.  
  
3. W  **\<Projekt > strony właściwości** okna dialogowego rozwiń **właściwości konfiguracji** węzeł, a następnie wybierz **debugowanie**.  
  
4. Ustaw **typ debugera** do **mieszane** lub **automatycznie**.  
  
## <a name="see-also"></a>Zobacz też  
 [Instrukcje: Debugowanie z projektu DLL](../debugger/how-to-debug-from-a-dll-project.md)
