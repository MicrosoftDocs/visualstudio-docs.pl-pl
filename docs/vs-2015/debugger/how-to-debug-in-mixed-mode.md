---
title: 'Instrukcje: debugowanie w trybie mieszanym | Microsoft Docs'
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
ms.openlocfilehash: c5e2dd4ea0000eefdbd9f74c8fa97c4c63e06fab
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "65681132"
---
# <a name="how-to-debug-in-mixed-mode"></a>Porady: debugowanie w trybie mieszanym
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Poniższe procedury opisują sposób debugowania kodu zarządzanego i natywnego, znanego również jako debugowanie w trybie mieszanym. Istnieją dwa scenariusze umożliwiające wykonanie tej czynności, w zależności od tego, czy biblioteka DLL lub aplikacja jest zapisywana w kodzie natywnym:  
  
- Aplikacja wywołująca, która wywołuje bibliotekę DLL, jest zapisywana w kodzie natywnym. W takim przypadku Biblioteka DLL jest zarządzana, a zarówno debugery zarządzane, jak i natywne muszą być włączone do debugowania obu. Możesz to sprawdzić w oknie dialogowym ** \<Project> strony właściwości** . Jak to zrobić, zależy od tego, czy rozpoczynasz debugowanie z projektu DLL lub projektu aplikacji wywołującej.  
  
- Wywoływana aplikacja wywołująca bibliotekę DLL jest zapisywana w kodzie zarządzanym, a Biblioteka DLL jest zapisywana w kodzie natywnym.  
  
> [!NOTE]
> Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić ustawienia, wybierz **Importuj i Eksportuj ustawienia** w menu **Narzędzia** . Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień deweloperskich w programie Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-enable-mixed-mode-debugging"></a>Aby włączyć debugowanie w trybie mieszanym  
  
1. W **Eksplorator rozwiązań**wybierz projekt.  
  
2. W menu **Widok** kliknij polecenie **strony właściwości**.  
  
3. W oknie dialogowym ** \<Project> strony właściwości** rozwiń węzeł **Właściwości konfiguracji** , a następnie wybierz pozycję **debugowanie**.  
  
4. Ustaw **Typ debugera** na **mieszany** lub **Auto**Auto.  
  
## <a name="see-also"></a>Zobacz też  
 [Instrukcje: debugowanie z projektu DLL](../debugger/how-to-debug-from-a-dll-project.md)
