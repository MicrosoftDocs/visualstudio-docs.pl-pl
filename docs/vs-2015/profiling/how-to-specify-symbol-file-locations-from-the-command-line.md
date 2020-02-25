---
title: 'Instrukcje: Określanie lokalizacji plików symboli z wiersza polecenia | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 8aa067bb-e8bf-4081-aff0-cfbcf65934a0
caps.latest.revision: 16
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 01fbb6cfd1717562af79c067ede0cad9753ad5dd
ms.sourcegitcommit: bf2e9d4ff38bf5b62b8af3da1e6a183beb899809
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/22/2020
ms.locfileid: "77557893"
---
# <a name="how-to-specify-symbol-file-locations-from-the-command-line"></a>Porady: określanie lokalizacji plików symboli z wiersza polecenia
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Aby wyświetlić informacje o symbolach, takie jak nazwy funkcji i numery wierszy, narzędzie wiersza polecenia VSPerfReport wymaga dostępu do plików symboli (. pdb) profilowanych składników i plików systemu Windows. Pliki symboli są tworzone podczas kompilowania składnika. Aby uzyskać więcej informacji, zobacz [VSPerfReport](../profiling/vsperfreport.md). VSPerfReport automatycznie przeszukuje następujące lokalizacje plików symboli:  
  
- Ścieżki określone w opcji **/SymbolPath** lub zmiennej środowiskowej **_NT_SYMBOL_PATH** .  
  
- Dokładna ścieżka lokalna, w której składnik został skompilowany.  
  
- Katalog zawierający plik danych profilowania (. vsp lub. vsps).  
  
  Firma Microsoft udostępnia pliki. pdb dla wielu produktów w trybie online na serwerze symboli. Jeśli komputer używany do raportowania jest połączony z Internetem, VSPerfReport nawiązuje połączenie z serwerem symboli online w celu automatycznego wyszukiwania informacji o symbolach i zapisywania plików w magazynie lokalnym.  
  
  Można określić lokalizację plików symboli i magazyn serwera symboli firmy Microsoft w następujący sposób:  
  
- Ustaw zmienną środowiskową **_NT_SYMBOL_PATH** .  
  
- Dodaj opcję **/SymbolPath** do wiersza polecenia VSPerfReport.  
  
  Można również użyć obu tych metod.  
  
> [!NOTE]
> Jeśli [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] jest zainstalowana na komputerze lokalnym, lokalizacja dla plików symboli systemu Windows prawdopodobnie została już określona. Aby uzyskać więcej informacji, zobacz [How to: Reference informacje o symbolach systemu Windows](../profiling/how-to-reference-windows-symbol-information.md). Nadal musisz skonfigurować VSPerfReport, aby używać lokalizacji i serwera zgodnie z opisem w dalszej części tego tematu.  
  
## <a name="specifying-windows-symbol-files"></a>Określanie plików symboli systemu Windows  
  
#### <a name="to-configure-the-use-of-the-windows-symbol-server"></a>Aby skonfigurować korzystanie z serwera symboli systemu Windows  
  
1. W razie potrzeby Utwórz katalog do przechowywania plików symboli lokalnie.  
  
2. Użyj następującej składni, aby ustawić zmienną środowiskową **_NT_SYMBOL_PATH** lub opcję VSPerfReport/SymbolPath:  
  
   `srv*<LocalStore>*https://msdl.microsoft.com/downloads/symbols`  
  
   gdzie *<LocalStore>* jest ścieżką utworzonego katalogu lokalnego.  
  
## <a name="specifying-component-symbol-files"></a>Określanie plików symboli składników  
 Narzędzia profilowania wyszukuje pliki. pdb składników, które mają być przełączone w ich oryginalnych lokalizacjach, które są przechowywane w składnikach lub w folderze, który zawiera plik danych profilowania. Możesz określić inne lokalizacje do przeszukania, dodając co najmniej jedną ścieżkę do **_NT_SYMBOL_PATH** lub opcji **/SymbolPath** . Rozdziel ścieżki średnikami.  
  
## <a name="example"></a>Przykład  
 Poniższy wiersz polecenia ustawia zmienną środowiskową **_NT_SYMBOL_PATH** na serwer symboli systemu Windows i katalog lokalny do **C:\symbols**.  

 ```cmd
 set  _NT_SYMBOL_PATH=srv*C:\symbols*https://msdl.microsoft.com/downloads/symbols
 ```

 Poniższy wiersz polecenia VSPerfReport dodaje katalog C:\Projects\Symbols do ścieżki wyszukiwania przy użyciu opcji **/SymbolPath** .  
  
 **VSPerfReport**  *MojaApl* **. exe/SymbolPath: C:\Projects\Symbols/Summary: ALL**
