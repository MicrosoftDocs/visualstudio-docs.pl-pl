---
title: Ustawienia projektu dla konfiguracji debugowania w języku VB | Microsoft Docs
ms.custom: seodec18
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bcac88c2faf1af7378ce25597789700df61648a9
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72730604"
---
# <a name="project-settings-for-a-visual-basic-debug-configuration"></a>Ustawienia projektu dla konfiguracji debugowania w Visual Basic
Ustawienia projektu dla konfiguracji debugowania [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] można zmienić w oknie **strony właściwości** , zgodnie z opisem w sekcji [debugowanie i wydawanie konfiguracji](../debugger/how-to-set-debug-and-release-configurations.md). W poniższych tabelach przedstawiono, gdzie znaleźć ustawienia związane z debugerem w oknie **strony właściwości** .

> [!WARNING]
> Ten temat nie dotyczy aplikacji platformy UWP. Zobacz [Rozpoczynanie sesji debugowania (VB, C# C++ i XAML)](../debugger/start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md)

### <a name="debug-tab"></a>Karta debugowanie

| Ustawienie | Opis |
|------------------------------| - |
| **Konfiguracja** | Tryb zestawów do kompilowania aplikacji. Wybierz spośród **aktywnych (Debuguj)** , **Debug**, **Release**, **All Configurations**. |
| **Uruchom akcję** | Ta grupa formantów określa akcję, która będzie wykonywana po wybraniu polecenia Rozpocznij z menu Debuguj.<br /><br /> -   **początkowy projekt** jest domyślnym i uruchamia projekt startowy na potrzeby debugowania. <br />-   **Uruchom program zewnętrzny** umożliwia uruchamianie i dołączanie do programu, który nie jest częścią [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] projektu. Aby uzyskać więcej informacji, zobacz [dołączanie do uruchomionych procesów](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).<br />-   **Uruchom przeglądarkę w adresie URL** umożliwia debugowanie aplikacji sieci Web. |
| **Argumenty wiersza polecenia** | Określa argumenty wiersza polecenia dla programu, który ma być debugowany. Nazwa polecenia to nazwa programu określona w początkowym programie zewnętrznym. Jeśli akcja uruchamiania jest ustawiona na początkowy adres URL, argumenty wiersza polecenia są ignorowane. |
| **Katalog roboczy** | Określa katalog roboczy debugowanego programu. W [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] katalog roboczy jest katalogiem, z którego aplikacja jest uruchamiana. Domyślny katalog roboczy to \bin\Debug lub \bin\Release, w zależności od bieżącej konfiguracji. |
| **Użyj maszyny zdalnej** | Gdy to pole wyboru jest zaznaczone, debugowanie zdalne jest włączone. W polu tekstowym można wpisać nazwę komputera zdalnego, na którym aplikacja będzie działać na potrzeby debugowania lub [nazwę serwera msvsmon](../debugger/remote-debugging.md). Lokalizacja EXE na komputerze zdalnym jest określana przez właściwość Ścieżka wyjściowa na karcie kompilacja. Lokalizacja musi być katalogiem udostępnionym na komputerze zdalnym. |
| **Debugowanie kodu niezarządzanego** | Umożliwia debugowanie wywołań natywnego (niezarządzanego) kodu Win32 z aplikacji zarządzanej. Jest to ten sam efekt, co wybranie opcji mieszane dla typu debugera w projekcie [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)]. |
| **Debugowanie SQL Server** | Umożliwia debugowanie obiektów SQL Server bazy danych. |

### <a name="compile-tab-press-advanced-compile-options-button"></a>Karta kompilacja: naciśnij przycisk Zaawansowane opcje kompilacji

| Ustawienie | Opis |
|---------------------------| - |
| **Włącz optymalizacje** | Ta opcja powinna być niezaznaczone. Optymalizacja powoduje, że kod, który jest faktycznie wykonywany, jest inny niż kod źródłowy widziany w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], co sprawia, że debugowanie jest trudne. Jeśli kod jest zoptymalizowany, symbole nie są ładowane domyślnie podczas debugowania za pomocą Tylko mój kod. |
| **Generuj informacje o debugowaniu** | Zdefiniowane domyślnie w wersji Debug i Release, to ustawienie (równoważne opcji kompilatora/Debug) tworzy informacje debugowania w czasie kompilacji. Debuger używa tych informacji do wyświetlania nazw zmiennych i innych informacji w przydatnym formularzu podczas debugowania. Jeśli kompilujesz program bez tych informacji, funkcjonalność debugera zostanie ograniczona. Aby uzyskać więcej informacji, zobacz [/Debug](/dotnet/visual-basic/reference/command-line-compiler/debug). |
| **Zdefiniuj stałą DEBUG** | Zdefiniowanie tego symbolu umożliwia warunkowe Kompilowanie funkcji wyjściowych z [klasy Debug](/dotnet/api/system.diagnostics.debug). Z tym zdefiniowanym symbolem metody klasy Debug generują dane wyjściowe do [okna danych wyjściowych](../ide/reference/output-window.md). Bez tego symbolu metody klasy debugowania nie są kompilowane i nie są generowane żadne dane wyjściowe. Ten symbol powinien być zdefiniowany w wersji Debug i nie jest zdefiniowany w wersji Release. Definiowanie tego symbolu w wersji wydanej powoduje utworzenie niepotrzebnego kodu, który spowalnia program. |
| **Zdefiniuj stałą TRACE** | Zdefiniowanie tego symbolu umożliwia warunkowe Kompilowanie funkcji wyjściowych z [klasy śledzenia](/dotnet/api/system.diagnostics.trace). Po zdefiniowaniu tego symbolu metody klasy śledzenia generują dane wyjściowe w [oknie danych wyjściowych](../ide/reference/output-window.md). Bez tego symbolu metody klasy śledzenia nie są kompilowane i nie są generowane żadne dane wyjściowe śledzenia. Ten symbol jest definiowany domyślnie dla wersji Debug i Release. |

## <a name="see-also"></a>Zobacz także
- [Ustawienia debugera i przygotowanie](../debugger/debugger-settings-and-preparation.md)