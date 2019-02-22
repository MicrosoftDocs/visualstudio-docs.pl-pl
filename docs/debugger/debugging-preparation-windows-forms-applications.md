---
title: Przygotowywanie do debugowania aplikacji Windows Forms | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 5cc06e33b3549bda9bdc9fe04073ca4cf0d9e9a5
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/22/2019
ms.locfileid: "56679948"
---
# <a name="debugging-preparation-windows-forms-applications"></a>Przygotowanie debugowania: Aplikacje Windows Forms
Szablon projektu Windows Forms tworzy aplikację Windows Forms. Debugowanie tego typu aplikacji w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] jest bardzo proste. Aby uzyskać więcej informacji, zobacz [Tworzenie projektu aplikacji Windows](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/42wc9kk5(v=vs.100)).

 Po utworzeniu projektu Windows Forms przy użyciu szablonu projektu [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] automatycznie tworzy wymagane ustawienia konfiguracji Debug i Release. Jeśli to konieczne, możesz zmienić te ustawienia. Te ustawienia można zmienić w programie  **\<Nazwa projektu > Właściwości strony** okno dialogowe (**mój projekt** w języku Visual Basic).

 Aby uzyskać więcej informacji, zobacz [zalecane ustawienia właściwości](../debugger/managed-debugging-recommended-property-settings.md).

 Poniższa tabela zawiera jedno dodatkowe właściwości zalecane ustawienie.

### <a name="configuration-properties-in-debug-tab"></a>Właściwości konfiguracji na karcie debugowania

|**Nazwa właściwości**|**Ustawienie**|
|-----------------------|-----------------|
|**Akcja uruchamiania**|-Ustaw **spustit projekt** większość czasu. Ustaw **uruchomienia programu zewnętrznego** jeśli ma być uruchamiany z innego pliku wykonywalnego po rozpoczęciu debugowania (zwykle na potrzeby debugowania bibliotek DLL).|

 Można debugować aplikacje Windows Forms z wewnątrz [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], lub przez dołączenie do już uruchomionego aplikacji. Aby uzyskać więcej informacji na temat dołączania, zobacz [dołączenia do uruchamiania procesów](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).

### <a name="to-debug-a-c-f-or-visual-basic-windows-forms-application"></a>Aby debugować C#, F#, lub aplikacji Visual Basic Windows Forms

1. Otwórz projekt w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].

2. Utwórz punkty przerwania, zgodnie z potrzebami.

    Ponieważ aplikacje Windows Forms są oparte na zdarzeniach, punktów przerwania przejdzie do kod procedury obsługi zdarzeń, lub metody wywoływane przez kod obsługi zdarzeń. Do typowych zdarzeń, w której chcesz umieścić punkty przerwania, obejmują:

   1. Zdarzenia związane z kontrolki, na przykład kliknij przycisk Enter, itp.

   2. Zdarzenia związane z aplikacji uruchamiania i zamykania, takich jak obciążenia, aktywowano itp.

   3. Fokus i zdarzenia sprawdzania poprawności.

      Aby uzyskać więcej informacji, zobacz [tworzenie obsługi zdarzeń w formularzach Windows Forms](/dotnet/framework/winforms/creating-event-handlers-in-windows-forms).

3. Na **debugowania** menu, kliknij przycisk **Start**.

4. Debugowanie za pomocą techniki opisane w [Pierwsze spojrzenie na debugera](../debugger/debugger-feature-tour.md).

## <a name="see-also"></a>Zobacz też
- [Debugowanie kodu zarządzanego](../debugger/debugging-managed-code.md)
- [Typy projektów C#, F# i Visual Basic](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)
- [Instrukcje: Ustawianie konfiguracji Debug i Release](../debugger/how-to-set-debug-and-release-configurations.md)
- [Ustawienia projektu dla konfiguracji debugowania w języku C#](../debugger/project-settings-for-csharp-debug-configurations.md)
- [Ustawienia projektu dla konfiguracji debugowania w języku Visual Basic](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)
- [Dołączanie do uruchomionego procesu](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)
- [Windows Forms](/dotnet/framework/winforms/index)