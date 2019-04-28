---
title: Pliki odpowiedzi MSBuild | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- response files, MSBuild
- MSBuild, response files
- MSBuild, .rsp files
- .rsp files
ms.assetid: 9f53987b-20ee-470a-ab62-fce997bb5e15
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9e83ed29e2caf180cdd8950b73f65f62794a8783
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63004845"
---
# <a name="msbuild-response-files"></a>Pliki odpowiedzi MSBuild
Odpowiedź (*rsp*) pliki to pliki tekstowe, które zawierają *MSBuild.exe* przełączniki wiersza polecenia. Każdy przełącznik może być w oddzielnym wierszu lub wszystkich przełączników mogą znajdować się na jeden wiersz. Komentarz wiersze są poprzedzone znakiem **#** symboli. **@** Przekazać inny plik odpowiedzi, który jest używany przełącznik *MSBuild.exe*.

## <a name="msbuildrsp"></a>MSBuild.rsp
Plik jest specjalny *rsp* pliku, który *MSBuild.exe* automatycznie używa podczas kompilowania projektu. Ten plik *MSBuild.rsp*, musi znajdować się w tym samym katalogu co *MSBuild.exe*, w przeciwnym razie go nie zostanie znaleziony. Możesz edytować ten plik, aby określić domyślny przełączniki wiersza polecenia do *MSBuild.exe*. Na przykład, jeśli używasz tego samego rejestrowania za każdym razem, gdy tworzysz projekt, można dodać **-rejestratora** przełączyć się do *MSBuild.rsp*, i *MSBuild.exe* użyje rejestratora każdym Projekt został skompilowany.

## <a name="directorybuildrsp"></a>Directory.Build.rsp
W wersji 15.6 i nowszym MSBuild wyszuka katalogi nadrzędne projektu dla pliku o nazwie *Directory.Build.rsp*.  Może to być przydatne w repozytorium kodu źródłowego w celu zapewnienia domyślnych argumentów podczas kompilacji z wiersza polecenia.  Może również służyć do określić argumenty wiersza polecenia hostowanych kompilacji.

## <a name="see-also"></a>Zobacz także
- [Odwołanie do narzędzia MSBuild](../msbuild/msbuild-reference.md)
- [Informacje dotyczące wiersza polecenia](../msbuild/msbuild-command-line-reference.md)