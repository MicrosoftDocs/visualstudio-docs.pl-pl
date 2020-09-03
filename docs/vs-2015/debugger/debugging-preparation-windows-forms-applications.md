---
title: 'Przygotowanie debugowania: aplikacje Windows Forms | Microsoft Docs'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "65691146"
---
# <a name="debugging-preparation-windows-forms-applications"></a>Przygotowanie debugowania: aplikacje Windows Forms
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Szablon projektu Windows Forms tworzy aplikację Windows Forms. Debugowanie tego typu aplikacji w programie [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] jest proste. Aby uzyskać więcej informacji, zobacz [Tworzenie projektu aplikacji systemu Windows](https://msdn.microsoft.com/b2f93fed-c635-4705-8d0e-cf079a264efa).  
  
 Podczas tworzenia projektu Windows Forms przy użyciu szablonu projektu program [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] automatycznie tworzy wymagane ustawienia dla konfiguracji debugowania i wydania. W razie potrzeby możesz zmienić te ustawienia. Te ustawienia można zmienić w oknie dialogowym ** \<project name> strony właściwości** (**mój projekt** w Visual Basic).  
  
 Aby uzyskać więcej informacji, zobacz [zalecane ustawienia właściwości](../debugger/managed-debugging-recommended-property-settings.md).  
  
 W poniższej tabeli przedstawiono jedno dodatkowe zalecane ustawienie właściwości.  
  
### <a name="configuration-properties-in-debug-tab"></a>Właściwości konfiguracji na karcie debugowanie  
  
|**Nazwa właściwości**|**Ustawienie**|  
|-----------------------|-----------------|  
|**Uruchom akcję**|-Ustaw **, aby uruchomić projekt,** w większości czasu. Ustaw, aby **uruchomić program zewnętrzny** , jeśli chcesz uruchomić inny plik wykonywalny po rozpoczęciu debugowania (zwykle dla debugowania bibliotek DLL).|  
  
 Można debugować Windows Forms aplikacje wewnątrz [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] lub dołączając do już działającej aplikacji. Aby uzyskać więcej informacji na temat dołączania, zobacz [dołączanie do uruchomionych procesów](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).  
  
### <a name="to-debug-a-c-f-or-visual-basic-windows-forms-application"></a>Aby debugować aplikację Windows Forms języka C#, F # lub Visual Basic  
  
1. Otwórz projekt w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .  
  
2. Utwórz punkty przerwania w razie konieczności.  
  
    Ponieważ Windows Forms aplikacje są sterowane zdarzeniami, punkty przerwania przechodzą w kod procedury obsługi zdarzeń lub do metod wywoływanych przez kod programu obsługi zdarzeń. Typowe zdarzenia, w których należy umieścić punkty przerwania, to m.in.:  
  
   1. Zdarzenia skojarzone z kontrolką, takie jak kliknięcie, wprowadzanie itd.  
  
   2. Zdarzenia skojarzone z uruchamianiem i zamykaniem aplikacji, takie jak ładowanie, aktywowane itd.  
  
   3. Zdarzenia fokusu i walidacji.  
  
      Aby uzyskać więcej informacji, zobacz [Tworzenie programów obsługi zdarzeń w Windows Forms](https://msdn.microsoft.com/library/6514e530-c6b8-489c-a8d2-eda7b7072701).  
  
3. W menu **debugowanie** kliknij przycisk **Uruchom**.  
  
4. Debuguj przy użyciu technik omówionych w [temacie podstawy debugera](../debugger/debugger-basics.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie kodu zarządzanego](../debugger/debugging-managed-code.md)   
 [Typy projektów C#, F # i Visual Basic](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)   
 [Instrukcje: Ustawianie konfiguracji debugowania i wydania](../debugger/how-to-set-debug-and-release-configurations.md)   
 [Ustawienia projektu dla konfiguracji debugowania w języku C#](../debugger/project-settings-for-csharp-debug-configurations.md)   
 [Ustawienia projektu dla konfiguracji debugowania Visual Basic](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)   
 [Dołącz do uruchomionych procesów](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)   
 [Windows Forms](https://msdn.microsoft.com/library/627df1e9-b254-41af-bbac-9a4f02810c54)
