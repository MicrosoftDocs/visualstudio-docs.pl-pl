---
title: 'Instrukcje: Określanie lokalizacji plików symboli z wiersza polecenia | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 8aa067bb-e8bf-4081-aff0-cfbcf65934a0
caps.latest.revision: 16
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e5ff4290d0cffa99a9f476c543626c5aa15be87a
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63436910"
---
# <a name="how-to-specify-symbol-file-locations-from-the-command-line"></a>Instrukcje: Określanie lokalizacji plików symboli z wiersza polecenia
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Aby wyświetlić informacje o symbolach, takich jak nazwy i numery wierszy, narzędzie wiersza polecenia VSPerfReport wymaga dostępu do plików symboli (.pdb) profilowanych składników i pliki systemu Windows. Pliki symboli są tworzone, gdy składnik został skompilowany. Aby uzyskać więcej informacji, zobacz [VSPerfReport](../profiling/vsperfreport.md). VSPerfReport automatycznie przeszukuje następujące lokalizacje plików symboli:  
  
- Ścieżki określane w **symbolpath** opcji lub **_NT_SYMBOL_PATH** zmiennej środowiskowej.  
  
- Gdy składnik został skompilowany dokładny ścieżka lokalna.  
  
- Katalog, który zawiera plik danych profilowania (.vsp lub .vsps).  
  
  Firma Microsoft udostępnia pliki .pdb dla wielu swoich produktów online na serwerze symboli. Jeśli komputer, którego używasz do raportowania jest połączony z Internetem, VSPerfReport łączy się z serwera symboli online, aby automatycznie wyszukać informacje o symbolach i Zapisz pliki w magazynie lokalnym.  
  
  Można określić lokalizacji plików symboli i magazynu serwera symboli firmy Microsoft w następujący sposób:  
  
- Ustaw **_NT_SYMBOL_PATH** zmiennej środowiskowej.  
  
- Dodaj **symbolpath** opcji wiersza polecenia VSPerfReport.  
  
  Można również użyć obu tych metod.  
  
> [!NOTE]
> Jeśli [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] jest zainstalowany na komputerze lokalnym, lokalizację, aby pliki symboli Windows prawdopodobnie określono już. Aby uzyskać więcej informacji, zobacz [jak: Informacje o symbolach Windows odwołanie](../profiling/how-to-reference-windows-symbol-information.md). Nadal należy skonfigurować VSPerfReport, aby użyć lokalizacji i serwera, zgodnie z opisem w dalszej części tego tematu.  
  
## <a name="specifying-windows-symbol-files"></a>Określanie plików symboli Windows  
  
#### <a name="to-configure-the-use-of-the-windows-symbol-server"></a>Umożliwia skonfigurowanie użycia serwera symboli Windows  
  
1. Jeśli to konieczne, należy utworzyć katalog do przechowywania plików symboli lokalnie.  
  
2. Użyj następującej składni, aby ustawić **_NT_SYMBOL_PATH** zmiennej środowiskowej lub opcji symbolpath VSPerfReport:  
  
    **srv\\*** *LocalStore* **\*http://msdl.microsoft.com/downloads/symbols**  
  
    gdzie *LocalStore* to ścieżka katalogu lokalnego, który został utworzony.  
  
## <a name="specifying-component-symbol-files"></a>Określanie plików symboli składnika  
 Profilowanie narzędzia wyszukuje pliki the.pdb składników, które chcesz przeprowadzić profilowanie w ich oryginalnych lokalizacji, które są przechowywane w składnikach lub w folderze, który zawiera plik danych profilowania. Można określić innych lokalizacji do przeszukania, dodając jeden lub więcej ścieżek do **_NT_SYMBOL_PATH** lub **symbolpath** opcji. Osobnym ścieżkom średnikami.  
  
## <a name="example"></a>Przykład  
 Następujące zestawy wiersza polecenia **_NT_SYMBOL_PATH** zmiennej środowiskowej, aby serwer symboli Windows i lokalnego katalogu, który **C:\Symbols**.  
  
 **Ustaw _NT_SYMBOL_PATH = srv\*C:\symbols\*http://msdl.microsoft.com/downloads/symbols**  
  
 Następujące polecenie w wierszu polecenia VSPerfReport dodaje C:\Projects\Symbols katalog do ścieżki wyszukiwania, używając **symbolpath** opcji.  
  
 **VSPerfReport***MyApp* **której /SymbolPath:C:\Projects\Symbols .exe**
