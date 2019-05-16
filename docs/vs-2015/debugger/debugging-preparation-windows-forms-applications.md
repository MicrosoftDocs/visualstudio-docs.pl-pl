---
title: 'Przygotowanie debugowania: Windows Forms aplikacji | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
- VB
- CSharp
helpviewer_keywords:
- debugging Windows applications
- Windows applications, debugging
- debugging [Visual Studio], Windows applications
- debugging [J#], Windows applications
- debugging [C#], Windows applications
- debugging [Visual Basic], Windows applications
ms.assetid: 7092ee7f-8378-4def-aef8-1695bd97cf14
caps.latest.revision: 31
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5b11855fbd19dc464f92b4339684ef8346556c21
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65691146"
---
# <a name="debugging-preparation-windows-forms-applications"></a>Przygotowanie debugowania: Aplikacje Windows Forms
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Szablon projektu Windows Forms tworzy aplikację Windows Forms. Debugowanie tego typu aplikacji w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] jest bardzo proste. Aby uzyskać więcej informacji, zobacz [Tworzenie projektu aplikacji Windows](https://msdn.microsoft.com/b2f93fed-c635-4705-8d0e-cf079a264efa).  
  
 Po utworzeniu projektu Windows Forms przy użyciu szablonu projektu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] automatycznie tworzy wymagane ustawienia konfiguracji Debug i Release. Jeśli to konieczne, możesz zmienić te ustawienia. Te ustawienia można zmienić w programie  **\<Nazwa projektu > Właściwości strony** okno dialogowe (**mój projekt** w języku Visual Basic).  
  
 Aby uzyskać więcej informacji, zobacz [zalecane ustawienia właściwości](../debugger/managed-debugging-recommended-property-settings.md).  
  
 Poniższa tabela zawiera jedno dodatkowe właściwości zalecane ustawienie.  
  
### <a name="configuration-properties-in-debug-tab"></a>Właściwości konfiguracji na karcie debugowania  
  
|**Nazwa właściwości**|**Ustawienie**|  
|-----------------------|-----------------|  
|**Akcja uruchamiania**|-Ustaw **spustit projekt** większość czasu. Ustaw **uruchomienia programu zewnętrznego** jeśli ma być uruchamiany z innego pliku wykonywalnego po rozpoczęciu debugowania (zwykle na potrzeby debugowania bibliotek DLL).|  
  
 Można debugować aplikacje Windows Forms z wewnątrz [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], lub przez dołączenie do już uruchomionego aplikacji. Aby uzyskać więcej informacji na temat dołączania, zobacz [dołączenia do uruchamiania procesów](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).  
  
### <a name="to-debug-a-c-f-or-visual-basic-windows-forms-application"></a>Aby debugować C#, F#, lub aplikacji Visual Basic Windows Forms  
  
1. Otwórz projekt w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
2. Utwórz punkty przerwania, zgodnie z potrzebami.  
  
    Ponieważ aplikacje Windows Forms są oparte na zdarzeniach, punktów przerwania przejdzie do kod procedury obsługi zdarzeń, lub metody wywoływane przez kod obsługi zdarzeń. Do typowych zdarzeń, w której chcesz umieścić punkty przerwania, obejmują:  
  
   1. Zdarzenia związane z kontrolki, na przykład kliknij przycisk Enter, itp.  
  
   2. Zdarzenia związane z aplikacji uruchamiania i zamykania, takich jak obciążenia, aktywowano itp.  
  
   3. Fokus i zdarzenia sprawdzania poprawności.  
  
      Aby uzyskać więcej informacji, zobacz [tworzenie obsługi zdarzeń w formularzach Windows Forms](https://msdn.microsoft.com/library/6514e530-c6b8-489c-a8d2-eda7b7072701).  
  
3. Na **debugowania** menu, kliknij przycisk **Start**.  
  
4. Debugowanie za pomocą techniki opisane w [podstawy debugera](../debugger/debugger-basics.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie zarządzanego kodu](../debugger/debugging-managed-code.md)   
 [C#, F#i typów projektów języka Visual Basic](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)   
 [Instrukcje: Ustaw wartość Debug i Release konfiguracji](../debugger/how-to-set-debug-and-release-configurations.md)   
 [Ustawienia projektu dla języka C# konfiguracji debugowania](../debugger/project-settings-for-csharp-debug-configurations.md)   
 [Ustawienia projektu dla języka Visual Basic konfiguracji debugowania](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)   
 [Dołączanie do uruchomionego procesu](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)   
 [Windows Forms](https://msdn.microsoft.com/library/627df1e9-b254-41af-bbac-9a4f02810c54)
