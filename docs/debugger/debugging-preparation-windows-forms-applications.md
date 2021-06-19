---
title: Przygotowanie do debugowania Windows Forms aplikacji | Microsoft Docs
description: Aby debugować aplikacje Windows Forms, które są tworzone przez szablon Windows Forms w programie Visual Studio, należy wykonać kroki Visual Studio.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: c2181fe0b0189b0c0472f4d7cadd6a7c8e172a9b
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2021
ms.locfileid: "112387752"
---
# <a name="debugging-preparation-windows-forms-applications"></a>Przygotowanie debugowania: aplikacje Windows Forms

Szablon Windows Forms aplikacji tworzy aplikację Windows Forms aplikacji. Debugowanie tego typu aplikacji w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] programie jest proste. Aby uzyskać informacje na temat tworzenia projektu tego typu, zobacz Create a Windows Form App (Tworzenie [aplikacji formularza systemu Windows).](../ide/create-csharp-winform-visual-studio.md)

 Podczas tworzenia projektu Windows Forms za pomocą szablonu projektu program automatycznie tworzy wymagane ustawienia dla konfiguracji [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] debugowania i wydania. W razie potrzeby można zmienić te ustawienia. Te ustawienia można zmienić w oknie dialogowym **\<project name> Strony właściwości** **(Mój projekt** w Visual Basic).

 Aby uzyskać więcej informacji, zobacz [Zalecane ustawienia właściwości](../debugger/managed-debugging-recommended-property-settings.md).

 W poniższej tabeli przedstawiono jedno dodatkowe zalecane ustawienie właściwości.

### <a name="configuration-properties-in-debug-tab"></a>Właściwości konfiguracji na karcie Debugowanie

|**Nazwa właściwości**|**Ustawienie**|
|-----------------------|-----------------|
|**Akcja uruchamiania**|— Ustaw **wartość Start project (Uruchom** projekt) przez większość czasu. Ustaw wartość **Uruchom program zewnętrzny,** jeśli chcesz uruchomić inny plik wykonywalny po rozpoczęciu debugowania (zazwyczaj w przypadku debugowania bibliotek DLL).|

 Aplikacje można debugować Windows Forms w programie lub przez [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] dołączenie do już uruchomionej aplikacji. Aby uzyskać więcej informacji na temat dołączania, zobacz [Dołączanie do uruchomionych procesów](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).

### <a name="to-debug-a-c-f-or-visual-basic-windows-forms-application"></a>Aby debugować aplikację w języku C#, F# Visual Basic Windows Forms aplikacji

1. Otwórz projekt w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .

2. Utwórz punkty przerwania zgodnie z potrzebami.

    Ponieważ Windows Forms są sterowane zdarzeniami, punkty przerwania będą trafiać do kodu procedury obsługi zdarzeń lub do metod wywoływanych przez kod procedury obsługi zdarzeń. Typowe zdarzenia, w których mają być umieszczane punkty przerwania, obejmują:

   1. Zdarzenia skojarzone z kontrolką, takie jak Kliknięcie, Enter itp.

   2. Zdarzenia skojarzone z uruchamianiem i zamykaniem aplikacji, takie jak Ładowanie, Aktywowane itp.

   3. Zdarzenia fokusu i walidacji.

      Aby uzyskać więcej informacji, zobacz Creating Event Handlers in Windows Forms (Tworzenie programów [obsługi zdarzeń w programie Windows Forms](/dotnet/framework/winforms/creating-event-handlers-in-windows-forms)).

3. W menu **Debug (Debugowanie)** kliknij pozycję Start **(Uruchom).**

4. Debuguj przy użyciu technik omówiowanych w [artykule Pierwsze spojrzenie na debuger](../debugger/debugger-feature-tour.md).

## <a name="see-also"></a>Zobacz też
- [Debugowanie zarządzanego kodu](../debugger/debugging-managed-code.md)
- [Typy projektów C#, F# i Visual Basic](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)
- [How to: Set Debug and Release Configurations](../debugger/how-to-set-debug-and-release-configurations.md)
- [Ustawienia projektu dla konfiguracji debugowania w języku C#](../debugger/project-settings-for-csharp-debug-configurations.md)
- [Ustawienia projektu dla konfiguracji Visual Basic debugowania](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)
- [Dołączanie do uruchomionych procesów](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)
- [Windows Forms](/dotnet/framework/winforms/index)