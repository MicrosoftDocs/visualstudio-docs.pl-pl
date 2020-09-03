---
title: Pliki odpowiedzi MSBuild | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
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
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a1ce11edac37368b9c4993a87a8c2b3e734b7862
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68189378"
---
# <a name="msbuild-response-files"></a>Pliki odpowiedzi MSBuild
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pliki odpowiedzi (. RSP) to pliki tekstowe, które zawierają MSBuild.exe przełączniki wiersza polecenia. Każdy przełącznik może znajdować się w osobnym wierszu lub wszystkie przełączniki mogą znajdować się w jednym wierszu. Wiersze komentarzy są poprzedzone **#** symbolem. **@** Przełącznik służy do przekazywania innego pliku odpowiedzi do MSBuild.exe.  
  
 Plik automatycznej odpowiedzi jest specjalnym plikiem RSP, który MSBuild.exe automatycznie używa podczas kompilowania projektu. Ten plik, MSBuild. rsp, musi znajdować się w tym samym katalogu co MSBuild.exe, w przeciwnym razie nie zostanie znaleziony. Można edytować ten plik, aby określić domyślne przełączniki wiersza polecenia do MSBuild.exe. Na przykład jeśli używasz tego samego rejestratora za każdym razem, gdy kompilujesz projekt, możesz dodać przełącznik **/Logger** do MSBuild. rsp, a MSBuild.exe będzie używać rejestratora za każdym razem, gdy projekt zostanie skompilowany.  
  
## <a name="see-also"></a>Zobacz też  
 [Dokumentacja programu MSBuild](../msbuild/msbuild-reference.md)   
 [Dokumentacja wiersza polecenia](../msbuild/msbuild-command-line-reference.md)
