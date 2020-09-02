---
title: Ustawienia stron właściwości dla projektów sieci Web | Microsoft Docs
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
- debugging [Visual Studio], Web applications
- project settings [Visual Studio], debug configurations
- debug builds, project settings
- projects [Visual Studio], debug configurations
- debugging Web applications, project settings
- debug configurations, Web projects
ms.assetid: 8ec5160a-6408-4f47-8d41-f0e20e79a3b9
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 3cb7cd3f8c3678d37feb2267f68ab5d2b3d970e0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68150852"
---
# <a name="property-pages-settings-for-web-projects"></a>Ustawienia stron właściwości dla projektów sieci Web
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ustawienia właściwości dla konfiguracji debugowania witryny sieci Web można zmienić w oknie dialogowym **strony właściwości** , zgodnie z opisem w sekcji [debugowanie i wydawanie konfiguracji](../debugger/how-to-set-debug-and-release-configurations.md). W poniższych tabelach przedstawiono, gdzie znaleźć ustawienia związane z debugerem w oknie dialogowym **strony właściwości** .  
  
### <a name="configuration-properties-folder-start-options-category"></a>Folder właściwości konfiguracji (kategoria opcji startowych)  
  
|**Ustawienie**|**Opis**|  
|-----------------|---------------------|  
|**Uruchom akcję**|Nagłówek, który grupuje opcje związane z uruchamianiem aplikacji.|  
|**Użyj bieżącej strony**|Określa bieżącą stronę jako punkt początkowy dla debugowania.|  
|**Określona Strona:**|Określa stronę sieci Web, w której chcesz rozpocząć debugowanie.|  
|**Uruchom program zewnętrzny:**|Określa polecenie do uruchamiania programu, który chcesz debugować.|  
|**Argumenty wiersza polecenia:**|Określa argumenty polecenia określonego powyżej.|  
|**Katalog roboczy:**|Określa katalog roboczy debugowanego programu. W programie [!INCLUDE[csprcs](../includes/csprcs-md.md)] katalog roboczy jest katalogiem, z którego aplikacja jest uruchamiana, domyślnie \bin\debug.|  
|**Początkowy adres URL**|Określa lokalizację aplikacji sieci Web, która ma być debugowana.|  
|**Nie otwieraj strony. Zaczekaj na żądanie z zewnętrznej aplikacji**|Mówi, że poczekaj na żądanie z zewnętrznej aplikacji. Ta opcja nie powoduje uruchomienia programu Internet Explorer lub innej aplikacji. Po prostu przygotowuje się do debugowania, gdy jest wywoływany przez aplikację.|  
|**Server** (Serwer)|Nagłówek, który grupuje opcje powiązane z serwerem, który ma być używany.|  
|**Użyj domyślnego serwera sieci Web**|Mówi, aby użyć domyślnego serwera sieci Web.|  
|**Użyj serwera niestandardowego**|Umożliwia wprowadzenie podstawowego adresu URL, który będzie używany jako serwer programu.|  
|**Debugery**|Nagłówek, który grupuje opcje związane z typem debugowania, który ma zostać wykonany.|  
|**Debugowanie ASP.NET**|Umożliwia debugowanie stron serwerowych pisanych dla [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] platformy deweloperskiej. Należy określić adres URL w polu **początkowy adres URL**.|  
|**Debugowanie kodu natywnego**|Umożliwia debugowanie wywołań natywnego (niezarządzanego) kodu Win32 z aplikacji zarządzanej.|  
|**Debugowanie SQL Server**|Umożliwia debugowanie obiektów SQL Server bazy danych.|  
|**Debugowanie Silverlight**|Umożliwia debugowanie składników Silverlight.|  
  
## <a name="see-also"></a>Zobacz też  
 [Ustawienia debugera i przygotowanie](../debugger/debugger-settings-and-preparation.md)
