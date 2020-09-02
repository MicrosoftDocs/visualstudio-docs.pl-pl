---
title: Ustawienia projektu dla konfiguracji debugowania w języku C# | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debug configurations, C#
- debugging [J#], debugger settings
- project settings [Visual Studio], debug configurations
- debug builds, project settings
- projects [Visual Studio], debug configurations
- project configurations, debug
- debugging [C#], debugger settings
- debug configurations, J#
ms.assetid: e30ca810-66e9-4d6e-9cf6-9f285cd0b100
caps.latest.revision: 25
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f1ec1c18fe92409a72994e4544215da01325d209
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "65687519"
---
# <a name="project-settings-for--c-debug-configurations"></a>Ustawienia projektu dla konfiguracji debugowania w C#
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ustawienia projektu dla konfiguracji debugowania języka C# można zmienić w oknie **strony właściwości** , zgodnie z opisem w sekcji [konfiguracje debugowania i wydania](../debugger/how-to-set-debug-and-release-configurations.md). W poniższych tabelach przedstawiono, gdzie znaleźć ustawienia związane z debugerem w oknie **strony właściwości** .  
  
> [!WARNING]
> Ten temat nie dotyczy aplikacji ze sklepu Windows. Zobacz [Rozpoczynanie sesji debugowania (VB, C#, C++ i XAML)](../debugger/start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md)  
  
## <a name="debug-tab"></a><a name="BKMK_Debug_tab"></a> Karta debugowanie  
  
|**Ustawienie**|**Opis**|  
|-----------------|---------------------|  
|**Konfiguracja**|Tryb zestawów do kompilowania aplikacji. Wybierz spośród **aktywnych (Debuguj)**, **Debug**, **Release**, **All Configurations**.|  
|**Uruchom akcję**|Ta grupa formantów określa akcję, która będzie wykonywana po wybraniu polecenia Rozpocznij z menu Debuguj.<br /><br /> -   **Początkowy projekt** jest domyślnie uruchamiany i uruchamia projekt startowy na potrzeby debugowania. Aby uzyskać więcej informacji, zobacz [Wybieranie projektu startowego](https://msdn.microsoft.com/222e3f32-a6fe-4941-bf37-6b2a921129fd).<br />-   **Uruchom program zewnętrzny** umożliwia uruchamianie i dołączanie do programu, który nie jest częścią [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] projektu. Aby uzyskać więcej informacji, zobacz [dołączanie do uruchomionego programu](https://msdn.microsoft.com/636d0a52-4bfd-48d2-89ad-d7b9ca4dc4f4).<br />-   Polecenie **Uruchom przeglądarkę w adresie URL** umożliwia debugowanie aplikacji sieci Web.|  
|**Argumenty wiersza polecenia**|Określa argumenty wiersza polecenia dla programu, który ma być debugowany. Nazwa polecenia to nazwa programu określona w początkowym programie zewnętrznym. Jeśli akcja uruchamiania jest ustawiona na początkowy adres URL, nie można określić argumentów wiersza polecenia.|  
|**Katalog roboczy**|Określa katalog roboczy debugowanego programu. W programie [!INCLUDE[csprcs](../includes/csprcs-md.md)] katalog roboczy jest katalogiem, w którym aplikacja jest domyślnie uruchamiana z \bin\debug.|  
|**Użyj maszyny zdalnej**|Nazwa komputera zdalnego, na którym aplikacja będzie działać na potrzeby debugowania lub [nazwy serwera msvsmon](https://msdn.microsoft.com/library/55b60ce7-834b-4e83-a10e-fe4248260a4c). Lokalizacja pliku EXE na komputerze zdalnym jest określana przez właściwość Ścieżka wyjściowa w folderze właściwości konfiguracji, Kategoria kompilacji. Lokalizacja musi być katalogiem udostępnionym na komputerze zdalnym.|  
|**Włącz debugowanie kodu niezarządzanego**|Umożliwia debugowanie wywołań natywnego (niezarządzanego) kodu Win32 z aplikacji zarządzanej.|  
|**Włącz debugowanie SQL Server**|Umożliwia debugowanie obiektów SQL Server bazy danych.|  
  
## <a name="build-tab"></a><a name="BKMK_Build_tab"></a> Karta kompilacja  
  
|Ustawienie|Opis|  
|-------------|-----------------|  
|**Symbole kompilacji warunkowej:**|W tym miejscu są zdefiniowane stałe debugowania i śledzenia.<br /><br /> Te stałe umożliwiają kompilację warunkową [klasy debugowania](https://msdn.microsoft.com/library/system.diagnostics.debug.aspx) i [klasy śledzenia](https://msdn.microsoft.com/library/system.diagnostics.trace.aspx). Dzięki tym stałym definicjom metody klasy Debug i Trace generują dane wyjściowe do [okna danych wyjściowych](../ide/reference/output-window.md). Bez tych stałych metody klasy Debug i Trace nie są kompilowane i nie są generowane żadne dane wyjściowe.<br /><br /> -Debugowanie jest zwykle zdefiniowane w wersji debugowej programu i niezdefiniowane w wersji.<br />-Trace jest zwykle zdefiniowane w wersjach Debug i Release.|  
|**Optymalizuj kod**|Jeśli nie znajdziesz błędu, który pojawia się tylko w zoptymalizowanym kodzie, należy pozostawić to ustawienie wyłączone w wersji Debug. Zoptymalizowany kod jest trudniejszy do debugowania, ponieważ instrukcje nie odpowiadają bezpośrednio na instrukcje w oknach źródłowych.|  
|**Ścieżka wyjściowa:**|Zwykle ustawiona na bin\Debug na potrzeby debugowania.|  
  
## <a name="see-also"></a>Zobacz też  
 [Ustawienia debugera i przygotowanie](../debugger/debugger-settings-and-preparation.md)
