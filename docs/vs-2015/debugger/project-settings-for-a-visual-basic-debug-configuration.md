---
title: Ustawienia dla konfiguracji debugowania w języku Visual Basic projektu | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 75d45f4aacad052d587950e5656dd74f153eba21
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63446139"
---
# <a name="project-settings-for-a-visual-basic-debug-configuration"></a>Ustawienia projektu dla konfiguracji debugowania w Visual Basic
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Można zmienić ustawienia projektu dla [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] konfiguracji debugowania w **stron właściwości** zgodnie z opisem w oknie [konfiguracji Debug i Release](../debugger/how-to-set-debug-and-release-configurations.md). W poniższej tabeli przedstawiono, gdzie można znaleźć ustawienia związane z debugerem w **stron właściwości** okna.  
  
> [!WARNING]
> Ten temat nie dotyczy Store aplikacji. Zobacz [uruchomić sesję debugowania (VB, C#, C++ i XAML)](../debugger/start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md)  
  
### <a name="debug-tab"></a>Debugowanie kartę  
  
|Ustawienie|Opis|  
|-------------|-----------------|  
|**Konfiguracja**|Ustawia tryb do kompilowania aplikacji. Można wybrać jedną z **aktywna (debugowanie)**, **debugowania**, **wersji**, **wszystkie konfiguracje**.|  
|**Akcja uruchamiania**|Ta grupa formantów Określa akcję, która ma miejsce, gdy z menu debugowanie wybierz przycisk Start.<br /><br /> -   **Rozpocznij projekt** jest ustawieniem domyślnym i uruchamia projekt startowy do debugowania. Aby uzyskać więcej informacji, zobacz [NIB jak: Ustaw projekty startowe](http://msdn.microsoft.com/31465836-0911-48db-a5d9-e456b635e970).<br />-   **Uruchom zewnętrzny program** pozwala uruchomić i Dołącz do programu, który nie jest częścią [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] projektu. Aby uzyskać więcej informacji, zobacz [dołączenia do uruchamiania procesów](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).<br />-   **Uruchom przeglądarkę w adresie URL** umożliwia debugowanie aplikacji sieci Web.|  
|**Argumenty wiersza polecenia**|Określa argumenty wiersza polecenia dla programu do debugowania. Nazwa polecenia jest nazwa programu, określone w uruchomienia programu zewnętrznego. Jeśli akcja uruchamiania jest ustawiony na początkowy adres URL, argumenty wiersza polecenia są ignorowane.|  
|**Katalog roboczy**|Określa katalog roboczy debugowanego programu. W [!INCLUDE[vbprvb](../includes/vbprvb-md.md)], katalog roboczy jest katalog, aplikacja zostanie uruchomiona z. Domyślny katalog roboczy jest \bin\Debug lub \bin\Release, w zależności od bieżącej konfiguracji.|  
|**Użyj komputera zdalnego**|Gdy pole wyboru jest zaznaczone, zdalne debugowanie jest włączone. W polu tekstowym, możesz wpisać nazwę komputera zdalnego, gdy aplikacja zostanie uruchomiona na potrzeby debugowania lub [nazwy serwera Msvsmon](http://msdn.microsoft.com/library/55b60ce7-834b-4e83-a10e-fe4248260a4c). Lokalizacja pliku EXE na komputerze zdalnym jest określona przez właściwość ścieżki wyjściowej na karcie kompilacji. Lokalizacja musi być możliwe do udostępnienia katalogu na komputerze zdalnym.|  
|**Debugowanie kodu niezarządzanego**|Umożliwia debugowanie wywołań do kodu natywnego (niezarządzanego) Win32 z zarządzanych aplikacji. Ma to taki sam skutek jak wybierać mieszany typ debugera w [!INCLUDE[vcprvc](../includes/vcprvc-md.md)] projektu.|  
|**Debugowanie serwera SQL Server**|Umożliwia debugowanie obiektów bazy danych programu SQL Server.|  
  
### <a name="compile-tab-press-advanced-compile-options-button"></a>Skompilować karta: kliknij przycisk Zaawansowane opcje kompilacji  
  
|Ustawienie|Opis|  
|-------------|-----------------|  
|**Włącz optymalizacje**|Tej opcji powinno być zaznaczone. Optymalizacja powoduje, że kod, który jest faktycznie wykonywane różnił się od kodu źródłowego w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]i w ten sposób sprawia, że debugowanie trudne. Jeśli kod jest zoptymalizowany, symbole nie są ładowane automatycznie podczas debugowania przy użyciu tylko mój kod.|  
|**Generuj informacje o debugowaniu**|Definiowane przez domyślne zarówno w przypadku debugowania, jak i wydania wersji, to ustawienie (równoważne/Debug — opcja kompilatora) tworzy informacje debugowania w czasie kompilacji. Debuger używa tych informacji, aby pokazać nazwy zmiennych i inne informacje w postaci przydatne podczas debugowania. Jeśli kompilujesz program bez tych informacji, debuger funkcjonalność będzie ograniczona. Aby uzyskać więcej informacji, zobacz [/debug](http://msdn.microsoft.com/library/c2b0bea5-1d5e-499f-9bd5-4f6c6b715ea2).|  
|**Zdefiniuj stałą DEBUG**|Definiowanie tego symbolu umożliwia kompilowanie warunkowe funkcji danych wyjściowych z [Klasa Debug](https://msdn.microsoft.com/library/system.diagnostics.debug.aspx). Z tego symbolu zdefiniowanego, metody klasy debugowania generują dane wyjściowe do [okno danych wyjściowych](../ide/reference/output-window.md). Bez tego symbolu metod klasy debugowania nie są kompilowane i generowane żadne dane wyjściowe. Ten symbol powinien być zdefiniowany w wersji do debugowania i nie jest zdefiniowany w pełnej wersji. Definiowanie tego symbolu w wersji tworzy zbędny kod, który spowalnia program.|  
|**Zdefiniuj stałą TRACE**|Definiowanie tego symbolu umożliwia kompilowanie warunkowe funkcji danych wyjściowych z [klasa śledzenia](https://msdn.microsoft.com/library/system.diagnostics.trace.aspx). Z tego symbolu zdefiniowanego, metody klasy śledzenia generują dane wyjściowe do [okno danych wyjściowych](../ide/reference/output-window.md). Bez tego symbolu metod klasy śledzenia nie są kompilowane i są generowane nie dane wyjściowe śledzenia. Ten symbol jest definiowany przez domyślne dla wersji zarówno Debug i Release.|  
  
## <a name="see-also"></a>Zobacz też  
 [Ustawienia debugera i przygotowanie](../debugger/debugger-settings-and-preparation.md)
