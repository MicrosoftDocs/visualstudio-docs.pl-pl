---
title: Określanie lokalizacji plików symboli z poziomu wiersza polecenia
description: Dowiedz się, jak narzędzie wiersza polecenia VSPerfReport wymaga dostępu do plików symboli (. pdb), aby wyświetlić informacje o symbolach, takie jak nazwy funkcji i numery wierszy.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 8aa067bb-e8bf-4081-aff0-cfbcf65934a0
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 1ea3eff001c49f4d7546985f1357126dc87717bc
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99920724"
---
# <a name="how-to-specify-symbol-file-locations-from-the-command-line"></a>Instrukcje: Określanie lokalizacji plików symboli z wiersza polecenia
Aby wyświetlić informacje o symbolach, takie jak nazwy funkcji i numery wierszy, narzędzie wiersza polecenia VSPerfReport wymaga dostępu do symbolu (.*PDB*) plików profilowanych składników i plików systemu Windows. Pliki symboli są tworzone podczas kompilowania składnika. Aby uzyskać więcej informacji, zobacz [VSPerfReport](../profiling/vsperfreport.md). VSPerfReport automatycznie przeszukuje następujące lokalizacje plików symboli:

- Ścieżki określone w opcji **/SymbolPath** lub zmiennej środowiskowej **_NT_SYMBOL_PATH** .

- Dokładna ścieżka lokalna, w której składnik został skompilowany.

- Katalog zawierający dane profilowania (.*VSP* lub. *vsps*) rozszerzeniem.

  Firma Microsoft zapewnia. pliki *PDB* dla wielu produktów w trybie online na serwerze symboli. Jeśli komputer używany do raportowania jest połączony z Internetem, VSPerfReport nawiązuje połączenie z serwerem symboli online w celu automatycznego wyszukiwania informacji o symbolach i zapisywania plików w magazynie lokalnym.

  Można określić lokalizację plików symboli i magazyn serwera symboli firmy Microsoft w następujący sposób:

- Ustaw zmienną środowiskową **_NT_SYMBOL_PATH** .

- Dodaj opcję **/SymbolPath** do wiersza polecenia VSPerfReport.

  Można również użyć obu tych metod.

> [!NOTE]
> Jeśli [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] program jest zainstalowany na komputerze lokalnym, prawdopodobnie określono już lokalizację plików symboli systemu Windows. Aby uzyskać więcej informacji, zobacz [How to: Reference informacje o symbolach systemu Windows](../profiling/how-to-reference-windows-symbol-information.md). Nadal musisz skonfigurować VSPerfReport, aby używać lokalizacji i serwera zgodnie z opisem w dalszej części tego tematu.

## <a name="specify-windows-symbol-files"></a>Określ pliki symboli systemu Windows

#### <a name="to-configure-the-use-of-the-windows-symbol-server"></a>Aby skonfigurować korzystanie z serwera symboli systemu Windows

1. W razie potrzeby Utwórz katalog do przechowywania plików symboli lokalnie.

2. Użyj następującej składni, aby ustawić zmienną środowiskową **_NT_SYMBOL_PATH** lub opcję VSPerfReport/SymbolPath:

    `srv*<LocalStore>*https://msdl.microsoft.com/download/symbols`

    gdzie *<LocalStore>* jest ścieżką utworzonego katalogu lokalnego.

## <a name="specify-component-symbol-files"></a>Określ pliki symboli składników
 Narzędzia profilowania wyszukuje. pliki *PDB* składników, które mają być przełączone w ich oryginalnych lokalizacjach, które są przechowywane w składnikach lub w folderze, który zawiera plik danych profilowania. Możesz określić inne lokalizacje do przeszukania, dodając co najmniej jedną ścieżkę do **_NT_SYMBOL_PATH** lub opcji **/SymbolPath** . Rozdziel ścieżki średnikami.

## <a name="example"></a>Przykład
 Poniższy wiersz polecenia ustawia zmienną środowiskową **_NT_SYMBOL_PATH** na serwer symboli systemu Windows i katalog lokalny do **C:\symbols**.

 ```cmd
  set  _NT_SYMBOL_PATH=srv*C:\symbols*https://msdl.microsoft.com/download/symbols
 ```

 Poniższy wiersz polecenia VSPerfReport dodaje katalog *C:\Projects\Symbols* do ścieżki wyszukiwania przy użyciu opcji **/SymbolPath** .

 **VSPerfReport**  *MojaApl* **. exe/SymbolPath: C:\Projects\Symbols/Summary: ALL**
