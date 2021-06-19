---
title: Ustawienia właściwości dla projektów internetowych | Microsoft Docs
description: W oknie dialogowym Strony właściwości okna dialogowego Strony właściwości okna dialogowego usługi Visual Studio.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 3e8a99e2c42ff14aba4bb31f087e55a0f1ebf3ae
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2021
ms.locfileid: "112386517"
---
# <a name="property-pages-settings-for-web-projects"></a>Ustawienia stron właściwości dla projektów sieci Web
Ustawienia właściwości konfiguracji debugowania witryny internetowej można  zmienić w oknie dialogowym Strony właściwości, zgodnie z omówieniem w artykule [Konfiguracje debugowania i wydania](../debugger/how-to-set-debug-and-release-configurations.md). W poniższych tabelach przedstawiono, gdzie można znaleźć ustawienia związane z debugerem w **oknie dialogowym Strony** właściwości.

### <a name="start-options-category"></a>Kategoria Opcje uruchamiania

| **Ustawienie** | **Opis** |
| - | - |
| **Akcja uruchamiania** | Nagłówek grupuje opcje związane z uruchamianiem aplikacji. |
| **Użyj bieżącej strony** | Określa bieżącą stronę jako punkt początkowy debugowania. |
| **Konk. Strona:** | Określa stronę sieci Web, na której chcesz rozpocząć debugowanie. |
| **Uruchom program zewnętrzny:** | Określa polecenie uruchamiania programu, który chcesz debugować. |
| **Argumenty wiersza polecenia:** | Określa argumenty dla polecenia określonego powyżej. |
| **Katalog roboczy:** | Określa katalog roboczy debugowany program. W programie katalog roboczy to katalog, z poziomu którym jest domyślnie uruchomiona [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] aplikacja, \bin\debug. |
| **Początkowy adres URL** | Określa lokalizację aplikacji internetowej, którą chcesz debugować. |
| **Nie otwieraj strony. Oczekiwanie na żądanie z aplikacji zewnętrznej** | Mówi, aby czekać na żądanie z aplikacji zewnętrznej. Ta opcja nie powoduje uruchomienia Internet Explorer lub innej aplikacji. Po prostu przygotowuje się do debugowania, gdy jest wywoływana przez aplikację. |
| **Server** (Serwer) | Nagłówek grupuje opcje powiązane z serwerem, który ma być używany. |
| **Użyj domyślnego serwera sieci Web** | Mówi, aby użyć domyślnego serwera sieci Web. |
| **Korzystanie z serwera niestandardowego** | Umożliwia wprowadzenie podstawowego adresu URL, który ma być serwerem. |
| **Debugery** | Nagłówek grupuje opcje związane z typem debugowania, które ma zostać wykonane. |
| **ASP.NET debugowania** | Umożliwia debugowanie stron serwera napisanych dla [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] platformy dewelopera. W polu Start **URL**(Adres URL startowy) należy określić adres URL . |
| **Debugowanie kodu natywnego** | Umożliwia debugowanie wywołań natywnego (nieza zarządzania) kodu Win32 z aplikacji zarządzanej. |
| **SQL Server debugowania** | Umożliwia debugowanie SQL Server bazy danych. |
| **Debugowanie programu Silverlight** | Umożliwia debugowanie składników programu Silverlight. |

## <a name="see-also"></a>Zobacz też
- [Ustawienia debugera i przygotowanie](../debugger/debugger-settings-and-preparation.md)