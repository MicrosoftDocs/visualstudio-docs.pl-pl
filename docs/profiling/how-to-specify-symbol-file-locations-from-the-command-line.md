---
title: 'Instrukcje: Określanie lokalizacji plików symboli z wiersza polecenia | Dokumentacja firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 8aa067bb-e8bf-4081-aff0-cfbcf65934a0
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0791019ce71a7d0fe6276ef9345284662ca31e00
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53917150"
---
# <a name="how-to-specify-symbol-file-locations-from-the-command-line"></a>Instrukcje: Określanie lokalizacji plików symboli z poziomu wiersza polecenia
Aby wyświetlić informacje o symbolach, takich jak nazwy i numery wierszy, narzędzie wiersza polecenia VSPerfReport wymaga dostępu do symbolu (. *plik PDB*) plików profilowanych składników i pliki systemu Windows. Pliki symboli są tworzone, gdy składnik został skompilowany. Aby uzyskać więcej informacji, zobacz [VSPerfReport](../profiling/vsperfreport.md). VSPerfReport automatycznie przeszukuje następujące lokalizacje plików symboli:  
  
- Ścieżki określane w **symbolpath** opcji lub **_NT_SYMBOL_PATH** zmiennej środowiskowej.  
  
- Gdy składnik został skompilowany dokładny ścieżka lokalna.  
  
- Katalog, który zawiera dane profilowania (. *Vsp* lub. *vsps*) pliku.  
  
  Firma Microsoft udostępnia. *pdb* plików dla wielu swoich produktów online na serwerze symboli. Jeśli komputer, którego używasz do raportowania jest połączony z Internetem, VSPerfReport łączy się z serwera symboli online, aby automatycznie wyszukać informacje o symbolach i Zapisz pliki w magazynie lokalnym.  
  
  Można określić lokalizacji plików symboli i magazynu serwera symboli firmy Microsoft w następujący sposób:  
  
- Ustaw **_NT_SYMBOL_PATH** zmiennej środowiskowej.  
  
- Dodaj **symbolpath** opcji wiersza polecenia VSPerfReport.  
  
  Można również użyć obu tych metod.  
  
> [!NOTE]
>  Jeśli [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] jest zainstalowany na komputerze lokalnym, lokalizację, aby pliki symboli Windows prawdopodobnie określono już. Aby uzyskać więcej informacji, zobacz [jak: Odwoływać się do informacji o symbolach Windows](../profiling/how-to-reference-windows-symbol-information.md). Należy jednak skonfigurować VSPerfReport, aby użyć lokalizacji i serwera, zgodnie z opisem w dalszej części tego tematu.  
  
## <a name="specify-windows-symbol-files"></a>Określ pliki symboli Windows  
  
#### <a name="to-configure-the-use-of-the-windows-symbol-server"></a>Umożliwia skonfigurowanie użycia serwera symboli Windows  
  
1. Jeśli to konieczne, należy utworzyć katalog do przechowywania plików symboli lokalnie.  
  
2. Użyj następującej składni, aby ustawić **_NT_SYMBOL_PATH** zmiennej środowiskowej lub opcji symbolpath VSPerfReport:  
  
    **SRV\\*** *LocalStore* **\*http://msdl.microsoft.com/downloads/symbols**  
  
    gdzie *LocalStore* to ścieżka katalogu lokalnego, który został utworzony.  
  
## <a name="specify-component-symbol-files"></a>Określanie plików symboli składnika  
 Wyszukuje narzędzi profilowania. *pdb* plików składników, które chcesz przeprowadzić profilowanie w ich oryginalnych lokalizacji, które są przechowywane w składnikach lub w folderze, który zawiera plik danych profilowania. Można określić innych lokalizacji do przeszukania, dodając jeden lub więcej ścieżek do **_NT_SYMBOL_PATH** lub **symbolpath** opcji. Osobnym ścieżkom średnikami.  
  
## <a name="example"></a>Przykład  
 Następujące zestawy wiersza polecenia **_NT_SYMBOL_PATH** zmiennej środowiskowej, aby serwer symboli Windows i lokalnego katalogu, który **C:\Symbols**.  
  
 **Ustaw _NT_SYMBOL_PATH = srv\*C:\symbols\*http://msdl.microsoft.com/downloads/symbols**  
  
 Dodaje następujące polecenie w wierszu polecenia VSPerfReport *C:\Projects\Symbols* katalog do ścieżki wyszukiwania przy użyciu **symbolpath** opcji.  
  
 **VSPerfReport***MyApp* **której /SymbolPath:C:\Projects\Symbols .exe**