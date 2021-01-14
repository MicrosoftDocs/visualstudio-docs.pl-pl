---
title: Ustawienia właściwości dla projektów sieci Web | Microsoft Docs
description: Dowiedz się, jak zmienić ustawienia właściwości dla konfiguracji debugowania witryny sieci Web w oknie dialogowym strony właściwości programu Visual Studio.
ms.custom: SEO-VS-2020, seodec18
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
ms.openlocfilehash: 86f15a6fa622bf7938740111705a295e09f3e443
ms.sourcegitcommit: a436ba564717b992eb1984b28ea0aec801eacaec
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/14/2021
ms.locfileid: "98205557"
---
# <a name="property-pages-settings-for-web-projects"></a>Ustawienia stron właściwości dla projektów sieci Web
Ustawienia właściwości dla konfiguracji debugowania witryny sieci Web można zmienić w oknie dialogowym **strony właściwości** , zgodnie z opisem w sekcji [debugowanie i wydawanie konfiguracji](../debugger/how-to-set-debug-and-release-configurations.md). W poniższych tabelach przedstawiono, gdzie znaleźć ustawienia związane z debugerem w oknie dialogowym **strony właściwości** .

### <a name="start-options-category"></a>Kategoria opcji uruchamiania

| **Ustawienie** | **Opis** |
| - | - |
| **Uruchom akcję** | Nagłówek, który grupuje opcje związane z uruchamianiem aplikacji. |
| **Użyj bieżącej strony** | Określa bieżącą stronę jako punkt początkowy dla debugowania. |
| **Określona Strona:** | Określa stronę sieci Web, w której chcesz rozpocząć debugowanie. |
| **Uruchom program zewnętrzny:** | Określa polecenie do uruchamiania programu, który chcesz debugować. |
| **Argumenty wiersza polecenia:** | Określa argumenty polecenia określonego powyżej. |
| **Katalog roboczy:** | Określa katalog roboczy debugowanego programu. W programie [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] katalog roboczy jest katalogiem, z którego aplikacja jest uruchamiana, domyślnie \bin\debug. |
| **Początkowy adres URL** | Określa lokalizację aplikacji sieci Web, która ma być debugowana. |
| **Nie otwieraj strony. Zaczekaj na żądanie z zewnętrznej aplikacji** | Mówi, że poczekaj na żądanie z zewnętrznej aplikacji. Ta opcja nie powoduje uruchomienia programu Internet Explorer lub innej aplikacji. Po prostu przygotowuje się do debugowania, gdy jest wywoływany przez aplikację. |
| **Server** (Serwer) | Nagłówek, który grupuje opcje powiązane z serwerem, który ma być używany. |
| **Użyj domyślnego serwera sieci Web** | Mówi, aby użyć domyślnego serwera sieci Web. |
| **Użyj serwera niestandardowego** | Umożliwia wprowadzenie podstawowego adresu URL, który będzie używany jako serwer programu. |
| **Debugery** | Nagłówek, który grupuje opcje związane z typem debugowania, który ma zostać wykonany. |
| **Debugowanie ASP.NET** | Umożliwia debugowanie stron serwerowych pisanych dla [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] platformy deweloperskiej. Należy określić adres URL w polu **początkowy adres URL**. |
| **Debugowanie kodu natywnego** | Umożliwia debugowanie wywołań natywnego (niezarządzanego) kodu Win32 z aplikacji zarządzanej. |
| **Debugowanie SQL Server** | Umożliwia debugowanie obiektów SQL Server bazy danych. |
| **Debugowanie Silverlight** | Umożliwia debugowanie składników Silverlight. |

## <a name="see-also"></a>Zobacz też
- [Ustawienia debugera i przygotowanie](../debugger/debugger-settings-and-preparation.md)