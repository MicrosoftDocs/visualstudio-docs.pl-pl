---
title: Ustawienia projektu dla konfiguracji debugowania Visual Basic | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vbProjectPropertiesDebug
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- project settings [Visual Studio], debug configurations
- debug builds, project settings
- debugging [Visual Basic], debugger settings
- projects [Visual Studio], debug configurations
- project configurations, debug
- debug configurations, Visual Basic
ms.assetid: 72a8483a-af0b-4403-8b0d-ee9ad71ee435
caps.latest.revision: 20
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 27acc89790e0759d3b284e3d9a4c6798c3d9a16f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "65687574"
---
# <a name="project-settings-for-a-visual-basic-debug-configuration"></a>Ustawienia projektu dla konfiguracji debugowania w Visual Basic
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ustawienia projektu dla [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] konfiguracji debugowania można zmienić w oknie **strony właściwości** , zgodnie z opisem w sekcji [konfiguracje debugowania i wydania](../debugger/how-to-set-debug-and-release-configurations.md). W poniższych tabelach przedstawiono, gdzie znaleźć ustawienia związane z debugerem w oknie **strony właściwości** .  
  
> [!WARNING]
> Ten temat nie dotyczy aplikacji ze sklepu. Zobacz [Rozpoczynanie sesji debugowania (VB, C#, C++ i XAML)](../debugger/start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md)  
  
### <a name="debug-tab"></a>Karta debugowanie  
  
|Ustawienie|Opis|  
|-------------|-----------------|  
|**Konfiguracja**|Tryb zestawów do kompilowania aplikacji. Wybierz spośród **aktywnych (Debuguj)**, **Debug**, **Release**, **All Configurations**.|  
|**Uruchom akcję**|Ta grupa formantów określa akcję, która będzie wykonywana po wybraniu polecenia Rozpocznij z menu Debuguj.<br /><br /> -   **Początkowy projekt** jest domyślnie uruchamiany i uruchamia projekt startowy na potrzeby debugowania. Aby uzyskać więcej informacji, zobacz [NIB How to: Set Start projects](https://msdn.microsoft.com/31465836-0911-48db-a5d9-e456b635e970).<br />-   **Uruchom program zewnętrzny** umożliwia uruchamianie i dołączanie do programu, który nie jest częścią [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] projektu. Aby uzyskać więcej informacji, zobacz [dołączanie do uruchomionych procesów](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).<br />-   Polecenie **Uruchom przeglądarkę w adresie URL** umożliwia debugowanie aplikacji sieci Web.|  
|**Argumenty wiersza polecenia**|Określa argumenty wiersza polecenia dla programu, który ma być debugowany. Nazwa polecenia to nazwa programu określona w początkowym programie zewnętrznym. Jeśli akcja uruchamiania jest ustawiona na początkowy adres URL, argumenty wiersza polecenia są ignorowane.|  
|**Katalog roboczy**|Określa katalog roboczy debugowanego programu. W programie [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] katalog roboczy jest katalogiem, z którego aplikacja jest uruchamiana. Domyślny katalog roboczy to \bin\Debug lub \bin\Release, w zależności od bieżącej konfiguracji.|  
|**Użyj maszyny zdalnej**|Gdy to pole wyboru jest zaznaczone, debugowanie zdalne jest włączone. W polu tekstowym można wpisać nazwę komputera zdalnego, na którym aplikacja będzie działać na potrzeby debugowania lub [nazwę serwera msvsmon](https://msdn.microsoft.com/library/55b60ce7-834b-4e83-a10e-fe4248260a4c). Lokalizacja EXE na komputerze zdalnym jest określana przez właściwość Ścieżka wyjściowa na karcie kompilacja. Lokalizacja musi być katalogiem udostępnionym na komputerze zdalnym.|  
|**Debugowanie kodu niezarządzanego**|Umożliwia debugowanie wywołań natywnego (niezarządzanego) kodu Win32 z aplikacji zarządzanej. Jest to ten sam efekt, co wybranie opcji mieszane dla typu debugera w [!INCLUDE[vcprvc](../includes/vcprvc-md.md)] projekcie.|  
|**Debugowanie SQL Server**|Umożliwia debugowanie obiektów SQL Server bazy danych.|  
  
### <a name="compile-tab-press-advanced-compile-options-button"></a>Karta kompilacja: naciśnij przycisk Zaawansowane opcje kompilacji  
  
|Ustawienie|Opis|  
|-------------|-----------------|  
|**Włącz optymalizacje**|Ta opcja powinna być niezaznaczone. Optymalizacja powoduje, że kod, który jest faktycznie wykonywany, różni się od kodu źródłowego widocznego w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] i w ten sposób utrudnia debugowanie. Jeśli kod jest zoptymalizowany, symbole nie są ładowane domyślnie podczas debugowania za pomocą Tylko mój kod.|  
|**Generuj informacje o debugowaniu**|Zdefiniowane domyślnie w wersji Debug i Release, to ustawienie (równoważne opcji kompilatora/Debug) tworzy informacje debugowania w czasie kompilacji. Debuger używa tych informacji do wyświetlania nazw zmiennych i innych informacji w przydatnym formularzu podczas debugowania. Jeśli kompilujesz program bez tych informacji, funkcjonalność debugera zostanie ograniczona. Aby uzyskać więcej informacji, zobacz [/Debug](https://msdn.microsoft.com/library/c2b0bea5-1d5e-499f-9bd5-4f6c6b715ea2).|  
|**Zdefiniuj stałą DEBUG**|Zdefiniowanie tego symbolu umożliwia warunkowe Kompilowanie funkcji wyjściowych z [klasy Debug](https://msdn.microsoft.com/library/system.diagnostics.debug.aspx). Z tym zdefiniowanym symbolem metody klasy Debug generują dane wyjściowe do [okna danych wyjściowych](../ide/reference/output-window.md). Bez tego symbolu metody klasy debugowania nie są kompilowane i nie są generowane żadne dane wyjściowe. Ten symbol powinien być zdefiniowany w wersji Debug i nie jest zdefiniowany w wersji Release. Definiowanie tego symbolu w wersji wydanej powoduje utworzenie niepotrzebnego kodu, który spowalnia program.|  
|**Zdefiniuj stałą TRACE**|Zdefiniowanie tego symbolu umożliwia warunkowe Kompilowanie funkcji wyjściowych z [klasy śledzenia](https://msdn.microsoft.com/library/system.diagnostics.trace.aspx). Po zdefiniowaniu tego symbolu metody klasy śledzenia generują dane wyjściowe w [oknie danych wyjściowych](../ide/reference/output-window.md). Bez tego symbolu metody klasy śledzenia nie są kompilowane i nie są generowane żadne dane wyjściowe śledzenia. Ten symbol jest definiowany domyślnie dla wersji Debug i Release.|  
  
## <a name="see-also"></a>Zobacz też  
 [Ustawienia debugera i przygotowanie](../debugger/debugger-settings-and-preparation.md)
