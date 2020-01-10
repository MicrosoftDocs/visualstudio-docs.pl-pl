---
title: Strony właściwości, JavaScript | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- javascript.project.property.debugging.debuggertype
- javascript.project.property.debugging.requireauthentication
- javascript.project.property.outputpath
- javascript.project.property.debugging.launchapplication
- javascript.project.property.defaultlanguage
- javascript.project.property.debugging.machinename
- javascript.project.property.debugging.allowlocalnetworkloopback
ms.assetid: a05ab01f-3d5d-4675-a845-eab51807d3a3
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e9fa22a4ed52c3e0a1afdda0105716c0de9b3316
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/10/2020
ms.locfileid: "75851812"
---
# <a name="property-pages-javascript"></a>Strony właściwości, JavaScript
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

**Strony właściwości**zapewniają dostęp do ustawień projektu. Możesz użyć stron, które są wyświetlane na **stronach właściwości** , aby zmienić właściwości projektu.

 Aby uzyskać dostęp do właściwości projektu, wybierz węzeł projektu w **Eksplorator rozwiązań**. W menu **projekt** kliknij polecenie **Właściwości**.

 [!INCLUDE[note_settings_general](../../includes/note-settings-general-md.md)]

 Na **stronach właściwości**są wyświetlane następujące strony i opcje.

## <a name="configuration-and-platform-page"></a>Strona konfiguracja i platforma
 Użyj następujących opcji, aby wybrać konfigurację i platformę do wyświetlenia lub zmodyfikowania.

 **Konfiguracja** Określa ustawienia konfiguracji do wyświetlenia lub zmodyfikowania. Ustawienia to **debugowanie** (domyślne), **wydanie**, **wszystkie konfiguracje**lub Konfiguracja zdefiniowana przez użytkownika. Aby uzyskać więcej informacji, zobacz [debugowanie i wydanie konfiguracji projektu](https://msdn.microsoft.com/0440b300-0614-4511-901a-105b771b236e).

 **Platforma** Określa ustawienia platformy do wyświetlenia lub zmodyfikowania. Ustawienia to **dowolny procesor** (domyślny dla aplikacji [!INCLUDE[win8_appname_long](../../includes/win8-appname-long-md.md)]), **x64**, **ARM**, **x86**lub platformy zdefiniowanej przez użytkownika. Aby uzyskać więcej informacji, zobacz [debugowanie i wydanie konfiguracji projektu](https://msdn.microsoft.com/0440b300-0614-4511-901a-105b771b236e).

## <a name="general-page"></a>Strona ogólna
 Użyj następujących opcji, aby ustawić ogólne właściwości projektu.

> [!NOTE]
> Niektóre opcje są dostępne tylko w aplikacjach ze sklepu Windows.

 **Ścieżka wyjściowa** Określa lokalizację plików wyjściowych dla konfiguracji projektu. Ścieżka jest względna; Jeśli wprowadzisz ścieżkę bezwzględną, ścieżka bezwzględna zostanie zapisana w projekcie. Ścieżka domyślna to bin\Debug.

 W przypadku korzystania z uproszczonych konfiguracji kompilacji system projektu określa, czy należy utworzyć wersję Debug lub Release. Gdy klikniesz pozycję **Debuguj**, **Rozpocznij debugowanie** (lub naciśnij klawisz F5), kompilacja jest umieszczana w lokalizacji debugowania niezależnie od określonej **ścieżki wyjściowej** . Jednak polecenie **Kompiluj rozwiązanie** w menu **kompilacja** umieszcza je w określonej lokalizacji. Aby włączyć zaawansowane konfiguracje kompilacji, na pasku menu wybierz **Narzędzia**, **Opcje**. W oknie dialogowym **Opcje** rozwiń węzeł **projekty i rozwiązania**, wybierz pozycję **Ogólne**, a następnie wyczyść pole wyboru **Pokaż zaawansowane konfiguracje kompilacji** . Zapewnia to ręczną kontrolę nad wszystkimi wartościami konfiguracji oraz o tym, czy została skompilowana wersja Debug lub Release. Aby uzyskać więcej informacji, zobacz [NIB: ogólne, projekty i rozwiązania, okno dialogowe Opcje](https://msdn.microsoft.com/8f8e37e8-b28d-4b13-bfeb-ea4d3312aeca).

 **Język domyślny** Określa język domyślny dla projektu. Opcja język wybrana w polu **zegar, język i region** w panelu sterowania Określa preferowany język użytkownika. Określając język domyślny dla projektu, należy upewnić się, że określone domyślne zasoby językowe są używane, jeśli preferowany język użytkownika nie jest zgodny z zasobami języka udostępnianymi w aplikacji.

## <a name="debug-page"></a>Strona debugowania
 Aby ustawić właściwości zachowania debugowania w projekcie, należy użyć następujących opcji.

> [!NOTE]
> Niektóre opcje są dostępne tylko w aplikacjach ze sklepu Windows.

 **Debuger do uruchomienia** Określa domyślnego hosta dla debugera.

- Wybierz pozycję **komputer lokalny** , aby uruchomić aplikację na komputerze hosta programu Visual Studio. Aby uzyskać więcej informacji, zobacz [Uruchamianie aplikacji na komputerze lokalnym](https://msdn.microsoft.com/library/windows/apps/hh441483(v=VS.85).aspx).

- Wybierz **symulator** , aby uruchomić aplikację w symulatorze. Aby uzyskać więcej informacji, zobacz [Uruchamianie aplikacji w symulatorze](https://msdn.microsoft.com/library/windows/apps/hh441475(v=VS.85).aspx).

- Wybierz pozycję **maszyna zdalna** , aby uruchomić aplikację na komputerze zdalnym. Aby uzyskać więcej informacji na temat debugowania zdalnego, zobacz [Uruchamianie aplikacji na komputerze zdalnym](https://msdn.microsoft.com/library/windows/apps/hh441469(v=VS.85).aspx).

  **Uruchom aplikację** Określa, czy uruchomić aplikację po naciśnięciu klawisza F5 lub kliknięciu przycisku **Debuguj**, **Rozpocznij debugowanie**. Wybierz pozycję **tak** , aby uruchomić aplikację. w przeciwnym razie wybierz pozycję **nie**. Jeśli wybierzesz opcję **nie**, nadal możesz debugować aplikację, jeśli używasz innej metody do jej uruchamiania.

  **Typ debugera** Określa typy kodu do debugowania. Wybierz opcję **tylko skrypt** , aby debugować kod JavaScript. Wybierz pozycję **zarządzane tylko** , aby debugować kod, który jest zarządzany przez środowisko uruchomieniowe języka wspólnego. Wybierz **tylko natywny** do C++ debugowania kodu. Wybierz opcję **natywny ze skryptem** , aby debugować C++ i JavaScript. Wybierz opcję **mieszany (zarządzany i natywny)** , aby debugować C++ kod zarządzany i.

  **Zezwalaj na sprzężenie zwrotne sieci lokalnej** Określa, czy dostęp do adresu IP sprzężenia zwrotnego jest dozwolony dla testowania aplikacji. Wybierz opcję **tak** , aby zezwolić na użycie adresu sprzężenia zwrotnego, jeśli aplikacja kliencka znajduje się na tym samym komputerze, na którym działa aplikacja serwera. w przeciwnym razie wybierz pozycję **nie**. Ta właściwość jest dostępna tylko wtedy, gdy właściwość **debuger do uruchomienia** jest ustawiona na **komputer zdalny**.

  **Nazwa maszyny** Określa nazwę komputera zdalnego do hostowania debugera. Ta właściwość jest dostępna tylko wtedy **, gdy debuger do uruchomienia** ma ustawioną **maszynę zdalną**.

  **Wymagaj uwierzytelniania** Określa, czy komputer zdalny wymaga uwierzytelniania. Ta właściwość jest dostępna tylko wtedy **, gdy debuger do uruchomienia** ma ustawioną **maszynę zdalną**.
