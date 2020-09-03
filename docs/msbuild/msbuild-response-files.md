---
title: Pliki odpowiedzi MSBuild | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "89315151"
---
# <a name="msbuild-response-files"></a>Pliki odpowiedzi MSBuild

Pliki odpowiedzi (*. rsp*) to pliki tekstowe, które zawierają *MSBuild.exe* przełączniki wiersza polecenia. Każdy przełącznik może znajdować się w osobnym wierszu lub wszystkie przełączniki mogą znajdować się w jednym wierszu. Wiersze komentarzy są poprzedzone **#** symbolem. **@** Przełącznik służy do przekazywania innego pliku odpowiedzi do *MSBuild.exe*.

## <a name="msbuildrsp"></a>MSBuild. rsp

Plik autoresponse jest specjalnym plikiem *RSP* , który *MSBuild.exe* automatycznie używa podczas kompilowania projektu. Ten plik, *MSBuild. rsp*, musi znajdować się w tym samym katalogu co *MSBuild.exe*, w przeciwnym razie nie zostanie znaleziony. Można edytować ten plik, aby określić domyślne przełączniki wiersza polecenia do *MSBuild.exe*. Na przykład jeśli używasz tego samego rejestratora za każdym razem, gdy kompilujesz projekt, możesz dodać przełącznik **-Rejestrator** do programu *MSBuild. rsp*, a *MSBuild.exe* będzie używać rejestratora za każdym razem, gdy projekt zostanie skompilowany.

## <a name="directorybuildrsp"></a>Katalog. Build. rsp

W wersji 15,6 i nowszych program MSBuild przeszuka katalogi nadrzędne projektu dla pliku o nazwie *Directory. Build. rsp*.  Może to być przydatne w repozytorium kodu źródłowego do dostarczania argumentów domyślnych podczas kompilacji w wierszu polecenia.  Można go również użyć do określenia argumentów wiersza polecenia dla kompilacji hostowanych.

## <a name="see-also"></a>Zobacz też

- [Dokumentacja programu MSBuild](../msbuild/msbuild-reference.md)
- [Dokumentacja wiersza polecenia](../msbuild/msbuild-command-line-reference.md)
