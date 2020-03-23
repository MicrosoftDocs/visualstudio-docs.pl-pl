---
title: MsBuild Pliki odpowiedzi | Dokumenty firmy Microsoft
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
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 44d6e3c77fee53b15ec8d18cb74fd7355ee101a8
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "79302897"
---
# <a name="msbuild-response-files"></a>Pliki odpowiedzi MSBuild

Pliki odpowiedzi (*.rsp*) to pliki tekstowe zawierające przełączniki wiersza polecenia *MSBuild.exe.* Każdy przełącznik może znajdować się na osobnej linii lub wszystkie przełączniki mogą być w jednej linii. Wiersze komentarza są poprzedzone **#** symbolem. Przełącznik **@** służy do przekazywania innego pliku odpowiedzi do *pliku MSBuild.exe*.

## <a name="msbuildrsp"></a>MSBuild.rsp

Plik autoresponse to specjalny plik *rsp,* którego *program MSBuild.exe* jest automatycznie używany podczas tworzenia projektu. Ten *plik, MSBuild.rsp*, musi znajdować się w tym samym katalogu co *MSBuild.exe*, w przeciwnym razie nie zostanie znaleziony. Można edytować ten plik, aby określić domyślne przełączniki wiersza polecenia na *msBuild.exe*. Na przykład jeśli używasz tego samego rejestratora przy każdym tworzeniu projektu, można dodać przełącznik **-logger** do *MSBuild.rsp*, a *MSBuild.exe użyje rejestratora* za każdym razem, gdy projekt jest zbudowany.

## <a name="directorybuildrsp"></a>Katalog.Build.rsp

W wersji 15.6 i wyższej MSBuild przeszukuje katalogi nadrzędne projektu dla pliku o nazwie *Directory.Build.rsp*.  Może to być przydatne w repozytorium kodu źródłowego, aby zapewnić domyślne argumenty podczas kompilacji wiersza polecenia.  Może również służyć do określania argumentów wiersza polecenia hostowanych kompilacji.

## <a name="see-also"></a>Zobacz też

- [Odwołanie do budynku MSBuild](../msbuild/msbuild-reference.md)
- [Odwołanie do wiersza polecenia](../msbuild/msbuild-command-line-reference.md)
