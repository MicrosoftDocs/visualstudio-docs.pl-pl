---
title: Przygotowywanie do debugowania aplikacji Windows Forms | Microsoft Docs
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging Windows applications
- Windows applications, debugging
- debugging [Visual Studio], Windows applications
- debugging [C#], Windows applications
- debugging [Visual Basic], Windows applications
ms.assetid: 7092ee7f-8378-4def-aef8-1695bd97cf14
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5ff927e5b917834341e442afa00e4acad4af2d2f
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72738095"
---
# <a name="debugging-preparation-windows-forms-applications"></a>Przygotowanie debugowania: aplikacje Windows Forms
Szablon projektu Windows Forms tworzy aplikację Windows Forms. Debugowanie tego typu aplikacji w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] jest proste. Aby uzyskać więcej informacji, zobacz [Tworzenie projektu aplikacji systemu Windows](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/42wc9kk5(v=vs.100)).

 Podczas tworzenia projektu Windows Forms przy użyciu szablonu projektu [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] automatycznie tworzy wymagane ustawienia dla konfiguracji debugowania i wydania. W razie potrzeby możesz zmienić te ustawienia. Te ustawienia można zmienić w oknie dialogowym **\<project nazwa > strony właściwości** (**mój projekt** w Visual Basic).

 Aby uzyskać więcej informacji, zobacz [zalecane ustawienia właściwości](../debugger/managed-debugging-recommended-property-settings.md).

 W poniższej tabeli przedstawiono jedno dodatkowe zalecane ustawienie właściwości.

### <a name="configuration-properties-in-debug-tab"></a>Właściwości konfiguracji na karcie debugowanie

|**Nazwa właściwości**|**Konfigurowania**|
|-----------------------|-----------------|
|**Uruchom akcję**|-Ustaw **, aby uruchomić projekt,** w większości czasu. Ustaw, aby **uruchomić program zewnętrzny** , jeśli chcesz uruchomić inny plik wykonywalny po rozpoczęciu debugowania (zwykle dla debugowania bibliotek DLL).|

 Można debugować Windows Forms aplikacje wewnątrz [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] lub przez dołączenie do już uruchomionej aplikacji. Aby uzyskać więcej informacji na temat dołączania, zobacz [dołączanie do uruchomionych procesów](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).

### <a name="to-debug-a-c-f-or-visual-basic-windows-forms-application"></a>Aby debugować Windows Forms C#aplikacji F#, lub Visual Basic

1. Otwórz projekt w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].

2. Utwórz punkty przerwania w razie konieczności.

    Ponieważ Windows Forms aplikacje są sterowane zdarzeniami, punkty przerwania przechodzą w kod procedury obsługi zdarzeń lub do metod wywoływanych przez kod programu obsługi zdarzeń. Typowe zdarzenia, w których należy umieścić punkty przerwania, to m.in.:

   1. Zdarzenia skojarzone z kontrolką, takie jak kliknięcie, wprowadzanie itd.

   2. Zdarzenia skojarzone z uruchamianiem i zamykaniem aplikacji, takie jak ładowanie, aktywowane itd.

   3. Zdarzenia fokusu i walidacji.

      Aby uzyskać więcej informacji, zobacz [Tworzenie programów obsługi zdarzeń w Windows Forms](/dotnet/framework/winforms/creating-event-handlers-in-windows-forms).

3. W menu **debugowanie** kliknij przycisk **Uruchom**.

4. Debuguj przy użyciu technik omówionych w [pierwszej kolejności w debugerze](../debugger/debugger-feature-tour.md).

## <a name="see-also"></a>Zobacz także
- [Debugowanie kodu zarządzanego](../debugger/debugging-managed-code.md)
- [Typy projektów C#, F# i Visual Basic](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)
- [Instrukcje: ustawienia konfiguracji Debug i Release](../debugger/how-to-set-debug-and-release-configurations.md)
- [Ustawienia projektu dla konfiguracji debugowania w języku C#](../debugger/project-settings-for-csharp-debug-configurations.md)
- [Ustawienia projektu dla konfiguracji debugowania w języku Visual Basic](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)
- [Dołączanie do uruchomionego procesu](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)
- [Windows Forms](/dotnet/framework/winforms/index)