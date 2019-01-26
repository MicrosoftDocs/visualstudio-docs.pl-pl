---
title: Ustawienia właściwości dla projektów sieci Web | Dokumentacja firmy Microsoft
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], Web applications
- project settings [Visual Studio], debug configurations
- debug builds, project settings
- projects [Visual Studio], debug configurations
- debugging Web applications, project settings
- debug configurations, Web projects
ms.assetid: 8ec5160a-6408-4f47-8d41-f0e20e79a3b9
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 809e84981bc491a89f8e031f5ac8caf497c1a6e6
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "55001972"
---
# <a name="property-pages-settings-for-web-projects"></a>Ustawienia stron właściwości dla projektów sieci Web
Możesz zmienić ustawienia właściwości dla konfiguracji debugowania witryny sieci web w **stron właściwości** okno dialogowe, zgodnie z opisem w [konfiguracji Debug i Release](../debugger/how-to-set-debug-and-release-configurations.md). W poniższej tabeli przedstawiono, gdzie można znaleźć ustawienia związane z debugerem w **stron właściwości** okno dialogowe.  
  
### <a name="start-options-category"></a>Kategoria opcji uruchamiania
  
| **Ustawienie** | **Opis** |
| - | - |
| **Akcja uruchamiania** | Nagłówek, że opcje grupy odnosi się do uruchomienia aplikacji. |
| **Bieżąca strona** | Określa bieżącą stronę jako punktu wyjścia do debugowania. |
| **Określona strona:** | Określa strony sieci Web, w którym chcesz rozpocząć debugowanie. |
| **Uruchom zewnętrzny program:** | Określa polecenia do uruchamiania programu, które chcesz debugować. |
| **Argumenty wiersza polecenia:** | Określa argumenty dla polecenia wymienione powyżej. |
| **Katalog roboczy:** | Określa katalog roboczy debugowanego programu. W [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)], katalog roboczy jest katalog, aplikacja zostanie uruchomiona z \bin\debug domyślny. |
| **Początkowy adres URL** | Określa lokalizację w aplikacji sieci Web, który chcesz debugować. |
| **Nie otwieraj strony. Czekaj na żądanie od aplikacji zewnętrznej** | Wynika z oczekiwania na żądanie od aplikacji zewnętrznej. Ta opcja nie zostanie uruchomiony program Internet Explorer lub innej aplikacji. Po prostu przygotowuje do debugowania, gdy zostanie wywołana przez aplikację. |
| **Serwer** | Nagłówek, że grupy opcje związane z serwera, który ma być używany. |
| **Użyj domyślnego serwera sieci Web** | Wyświetlana jest informacja użyć domyślnego serwera sieci Web. |
| **Użyj niestandardowego serwera** | Umożliwia wprowadzenie podstawowy adres URL do użycia jako serwer. |
| **Debugery** | Pozycja opcji grupy powiązany typ debugowania do wykonania. |
| **Debugowanie ASP.NET** | Włącza debugowanie stron ASP napisane dla [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] platformy deweloperskiej. Należy określić adres URL w **początkowy adres URL**. |
| **Debugowanie kodu natywnego** | Umożliwia debugowanie wywołań do kodu natywnego (niezarządzanego) Win32 z zarządzanych aplikacji. |
| **Debugowanie serwera SQL Server** | Umożliwia debugowanie obiektów bazy danych programu SQL Server. |
| **Debugowanie Silverlight** | Umożliwia debugowanie Silverlight składników. |
  
## <a name="see-also"></a>Zobacz też  
 [Ustawienia debugera i przygotowanie](../debugger/debugger-settings-and-preparation.md)