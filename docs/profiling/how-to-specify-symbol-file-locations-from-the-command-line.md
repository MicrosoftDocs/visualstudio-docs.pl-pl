---
title: 'Jak: Określanie lokalizacji plików symboli z wiersza polecenia | Dokumenty firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 8aa067bb-e8bf-4081-aff0-cfbcf65934a0
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 604863cbef5e42b31450ea09dffa56a1a00ae992
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "77476886"
---
# <a name="how-to-specify-symbol-file-locations-from-the-command-line"></a>Jak: Określanie lokalizacji plików symboli z wiersza polecenia
Aby wyświetlić informacje o symbolu, takie jak nazwy funkcji i numery wierszy, narzędzie wiersza polecenia VSPerfReport wymaga dostępu do symbolu (.* pdb)* plików profilowanych komponentów i plików systemowych Windows. Pliki symboli są tworzone podczas kompilowania składnika. Aby uzyskać więcej informacji, zobacz [VSPerfReport](../profiling/vsperfreport.md). VsPerfReport automatycznie przeszukuje następujące lokalizacje w poszukiwaniu plików symboli:

- Ścieżki określone w **/SymbolPath** opcji lub w **_NT_SYMBOL_PATH** zmiennej środowiskowej.

- Dokładna ścieżka lokalna, w której składnik został skompilowany.

- Katalog zawierający dane profilowania (.* vsp* lub . *vsps*) Plik.

  Firma Microsoft udostępnia plik . *pliki pdb* dla wielu swoich produktów online na serwerze symboli. Jeśli komputer używany do raportowania jest połączony z Internetem, program VSPerfReport łączy się z serwerem symboli online, aby automatycznie wyszukać informacje o symbolu i zapisać pliki w magazynie lokalnym.

  Lokalizację plików symboli i magazynu serwera symboli firmy Microsoft można określić w następujący sposób:

- Ustaw **_NT_SYMBOL_PATH** zmienną środowiskową.

- Dodaj opcję **/SymbolPath** do wiersza polecenia VSPerfReport.

  Można również użyć obu tych metod.

> [!NOTE]
> Jeśli [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] jest zainstalowany na komputerze lokalnym, lokalizacja dla plików symboli systemu Windows prawdopodobnie została już określona. Aby uzyskać więcej informacji, zobacz [Jak: Odwoływanie się do informacji o symbolu systemu Windows](../profiling/how-to-reference-windows-symbol-information.md). Nadal należy skonfigurować VSPerfReport używać lokalizacji i serwera, jak opisano w dalszej części tego tematu.

## <a name="specify-windows-symbol-files"></a>Określanie plików symboli systemu Windows

#### <a name="to-configure-the-use-of-the-windows-symbol-server"></a>Aby skonfigurować korzystanie z serwera symboli systemu Windows

1. W razie potrzeby utwórz katalog do lokalnego przechowywania plików symboli.

2. Aby ustawić _NT_SYMBOL_PATH zmienną środowiskową **lub** vsPerfReport /SymbolPath, należy użyć następującej składni:

    `srv*<LocalStore>*https://msdl.microsoft.com/download/symbols`

    gdzie *<LocalStore>* znajduje się ścieżka utworzonego katalogu lokalnego.

## <a name="specify-component-symbol-files"></a>Określanie plików symboli komponentu
 Narzędzia profilowania wyszukuje. *pliki pdb* składników, które mają być profilowane w ich oryginalnych lokalizacjach, które są przechowywane w składnikach lub w folderze zawierającym plik danych profilowania. Można określić inne lokalizacje do wyszukiwania, dodając jedną lub więcej ścieżek do **_NT_SYMBOL_PATH** lub do **/SymbolPath** opcji. Oddzielne ścieżki z średnikami.

## <a name="example"></a>Przykład
 Następujący wiersz polecenia ustawia **zmienną** środowiskową _NT_SYMBOL_PATH na serwer symboli systemu Windows, a katalog lokalny na **C:\Symbols**.

 ```cmd
  set  _NT_SYMBOL_PATH=srv*C:\symbols*https://msdl.microsoft.com/download/symbols
 ```

 Następujący wiersz polecenia VSPerfReport dodaje katalog *C:\Projects\Symbols* do ścieżki wyszukiwania przy użyciu opcji **/SymbolPath.**

 **VSPerfReport**  *MyApp* **.exe /SymbolPath:C:\Projekty\Symbole /summary:all**
