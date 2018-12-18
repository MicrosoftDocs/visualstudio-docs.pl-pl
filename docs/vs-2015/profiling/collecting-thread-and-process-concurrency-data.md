---
title: Zbieranie danych współbieżności procesu i wątku | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- concurrency profiling method
- Profiling Tools, concurrency method
ms.assetid: fa03d381-a9ee-408c-876d-05111e29225b
caps.latest.revision: 19
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: df473bea51edd157e3856d274663b72dcc11bc23
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51762618"
---
# <a name="collecting-thread-and-process-concurrency-data"></a>Zbieranie danych współbieżności dla wątku i procesu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Metoda profilowania współbieżności Profiling Tools umożliwia zbieranie danych rywalizacji zasobów, który zawiera informacje na temat każdego zdarzenia synchronizacji, który powoduje, że funkcji w profilowanej aplikacji, aby czekać na dostęp do zasobu.  
  
 **Wymagania**  
  
- [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
  Można określić współbieżności, metoda profilowania przy użyciu jednej z następujących procedur:  
  
- Na pierwszej stronie kreatora profilowania, kliknij przycisk **współbieżności**  
  
- Na **ogólne** strony okna dialogowego właściwości sesji wydajności, kliknij przycisk **współbieżności**.  
  
- Na **Eksplorator wydajności** narzędzi w **metoda** kliknij **współbieżności**.  
  
## <a name="common-tasks"></a>Typowe zadania  
 Można określić dodatkowe opcje w _sesji wydajności_**stron właściwości** okna dialogowego sesji wydajności. Aby otworzyć to okno dialogowe:  
  
- W **Eksplorator wydajności**, kliknij prawym przyciskiem myszy nazwę sesji wydajności, a następnie kliknij **właściwości**.  
  
  Zadania przedstawione w poniższej tabeli opisano opcje, które można określić w _sesji wydajności_**stron właściwości** okno dialogowe podczas profilowania za pomocą metody współbieżności.  
  
|Zadanie|Powiązana zawartość|  
|----------|---------------------|  
|Na **ogólne** Określ szczegóły nazewnictwa dla wygenerowanego pliku danych (Vsp) profilowania.|-   [Porady: Ustawianie opcji nazwy pliku danych wydajności](../profiling/how-to-set-performance-data-file-name-options.md)|  
|Na **Uruchom** Określ aplikację do uruchomienia, jeśli masz wiele projektów .exe w rozwiązaniu kodu.|-   [Porady: Określanie plików binarnych do ekranu startowego](../profiling/how-to-specify-the-binary-to-start.md)|  
|Na **funkcję Tier Interaction** strony, należy dodać danych połączeń ADO.NET do uruchomienia profilowania.|-   [Zbieranie danych o interakcji między warstwami](../profiling/collecting-tier-interaction-data.md)|  
|Na **liczniki Windows** stronie Określ co najmniej jeden licznik wydajności systemu operacyjnego można dodać do danych profilowania jako znaki.|-   [Porady: zbieranie danych licznika Windows](../profiling/how-to-collect-windows-counter-data.md)|  
|Na **zaawansowane** Określ wersję środowiska wykonawczego .NET Framework do profilowania, jeśli moduły aplikacji używać wielu wersji. Domyślnie jest profilowane pierwszej wersji załadowane.|-   [Porady: Określanie środowiska wykonawczego .NET Framework](../profiling/how-to-specify-the-dotnet-framework-runtime.md)|



