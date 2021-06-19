---
title: Ustawienia projektu dla konfiguracji debugowania WB | Microsoft Docs
description: Dowiedz się, jak zmienić ustawienia projektu dla konfiguracji Visual Basic debugowania w oknie Strony właściwości Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vbProjectPropertiesDebug
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- project settings [Visual Studio], debug configurations
- debug builds, project settings
- debugging [Visual Basic], debugger settings
- projects [Visual Studio], debug configurations
- project configurations, debug
- debug configurations, Visual Basic
ms.assetid: 72a8483a-af0b-4403-8b0d-ee9ad71ee435
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: f16d0dde62a23d8272cb89aec46f2ce952f18979
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2021
ms.locfileid: "112385214"
---
# <a name="project-settings-for-a-visual-basic-debug-configuration"></a>Ustawienia projektu dla konfiguracji debugowania w Visual Basic
Ustawienia projektu dla konfiguracji debugowania można zmienić w oknie Strony właściwości, zgodnie z omówieniem w [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] artykule [Konfiguracje debugowania i wydania](../debugger/how-to-set-debug-and-release-configurations.md).  W poniższych tabelach przedstawiono, gdzie można znaleźć ustawienia związane z debugerem w **oknie Strony** właściwości.

> [!WARNING]
> Ten temat nie dotyczy aplikacji platformy UWP. Zobacz [Rozpoczynanie sesji debugowania (VB, C#, C++ i XAML)](../debugger/start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md)

### <a name="debug-tab"></a>Karta Debugowanie

| Ustawienie | Opis |
|------------------------------| - |
| **Konfiguracja** | Ustawia tryb kompilowania aplikacji. Wybierz jedną z **opcji: Aktywne (debugowanie),** **Debugowanie,** **Wydanie,** **Wszystkie konfiguracje.** |
| **Akcja uruchamiania** | Ta grupa kontrolek określa akcję, która będzie występować po wybraniu pozycji Uruchom z menu Debugowanie.<br /><br /> -   **Projekt startowy** jest domyślny i uruchamia projekt startowy na potrzeby debugowania. <br />-   **Uruchamianie programu zewnętrznego** umożliwia uruchamianie i dołączanie do programu, który nie jest częścią [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] projektu. Aby uzyskać więcej informacji, zobacz [Attach to Running Processes (Dołączanie do uruchomionych procesów).](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)<br />-   **Przeglądarka Start w adresie URL** umożliwia debugowanie aplikacji internetowej. |
| **Argumenty wiersza polecenia** | Określa argumenty wiersza polecenia dla programu do debugowania. Nazwa polecenia jest nazwą programu określoną w Start programu zewnętrznego. Jeśli akcja uruchamiania jest ustawiona na startowy adres URL, argumenty wiersza polecenia są ignorowane. |
| **Katalog roboczy** | Określa katalog roboczy debugowany program. W [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] programie katalog roboczy to katalog, z którym jest uruchomiona aplikacja. Domyślny katalog roboczy to \bin\Debug lub \bin\Release, w zależności od bieżącej konfiguracji. |
| **Korzystanie z maszyny zdalnej** | Gdy to pole wyboru jest zaznaczone, debugowanie zdalne jest włączone. W polu tekstowym możesz wpisać nazwę maszyny zdalnej, na której aplikacja będzie uruchamiana na potrzeby debugowania, lub nazwę [serwera Msvsmon](../debugger/remote-debugging.md). Lokalizacja pliku EXE na maszynie zdalnej jest określona przez właściwość Ścieżka danych wyjściowych na karcie Kompilacja. Lokalizacja musi być katalogiem współużytkowalnym na maszynie zdalnej. |
| **Debugowanie kodu niezabędowego** | Umożliwia debugowanie wywołań natywnego (nieza zarządzania) kodu Win32 z aplikacji zarządzanej. Ma to taki sam efekt jak wybranie opcji Mixed (Mieszany) dla ustawienia Debugger Type (Typ [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] debugera) w projekcie. |
| **SQL Server debugowania** | Umożliwia debugowanie SQL Server bazy danych. |

### <a name="compile-tab-press-advanced-compile-options-button"></a>Karta Kompilacja: naciśnij przycisk Zaawansowane opcje kompilacji

| Ustawienie | Opis |
|---------------------------| - |
| **Włączanie optymalizacji** | Ta opcja powinna być niezaznaczone. Optymalizacja powoduje, że kod, który jest faktycznie wykonywany, różni się od kodu źródłowego widocznego w pliku , co utrudnia [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] debugowanie. Jeśli kod jest zoptymalizowany, symbole nie są ładowane domyślnie podczas debugowania przy użyciu Tylko mój kod. |
| **Generowanie informacji o debugowaniu** | To ustawienie (równoważne opcji kompilatora /debug) domyślnie w wersjach debugowania i wydania tworzy informacje debugowania w czasie kompilacji. Debuger używa tych informacji do pokazywania nazw zmiennych i innych informacji w przydatnym formularzu podczas debugowania. W przypadku skompilowania programu bez tych informacji funkcjonalność debugera będzie ograniczona. Aby uzyskać więcej informacji, zobacz [/debug](/dotnet/visual-basic/reference/command-line-compiler/debug). |
| **Definiowanie stałej DEBUG** | Zdefiniowanie tego symbolu umożliwia warunkowe kompilowanie funkcji wyjściowych z [klasy Debug](/dotnet/api/system.diagnostics.debug). Po zdefiniowanym symbolu metody klasy debugowania generują dane wyjściowe w [oknie Dane wyjściowe](../ide/reference/output-window.md). Bez tego symbolu metody klasy debugowania nie są kompilowane i nie są generowane żadne dane wyjściowe. Ten symbol powinien być zdefiniowany w wersji debugowania i nie powinien być zdefiniowany w wersji release. Zdefiniowanie tego symbolu w wersji wydania powoduje utworzenie niepotrzebnego kodu, który spowalnia program. |
| **Definiowanie stałej TRACE** | Zdefiniowanie tego symbolu umożliwia warunkowe kompilowanie funkcji wyjściowych z [klasy Trace](/dotnet/api/system.diagnostics.trace). Po zdefiniowanym symbolu metody klasy Trace generują dane wyjściowe w [oknie Dane wyjściowe](../ide/reference/output-window.md). Bez tego symbolu metody klasy Trace nie są kompilowane i nie są generowane żadne dane wyjściowe śledzenia. Ten symbol jest zdefiniowany domyślnie zarówno dla wersji debugowania, jak i wersji wydania. |

## <a name="see-also"></a>Zobacz też
- [Ustawienia debugera i przygotowanie](../debugger/debugger-settings-and-preparation.md)