---
title: Pliki odpowiedzi MSBuild | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 9168582d5bfc97dc657fb7a9b867459cb08c90a1
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54770726"
---
# <a name="msbuild-response-files"></a>Pliki odpowiedzi MSBuild
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Pliki odpowiedzi (rsp) to pliki tekstowe, zawierające MSBuild.exe przełączniki wiersza polecenia. Każdy przełącznik może być w oddzielnym wierszu lub wszystkich przełączników mogą znajdować się na jeden wiersz. Komentarz wiersze są poprzedzone znakiem **#** symboli. **@** Jest używany przełącznik, aby przekazać inny plik odpowiedzi do MSBuild.exe.  
  
 Plik automatyczne odpowiedzi jest plikiem rsp specjalne, które MSBuild.exe automatycznie będą używać podczas kompilowania projektu. Ten plik, MSBuild.rsp, musi być w tym samym katalogu co MSBuild.exe, w przeciwnym razie go nie zostanie znaleziony. Możesz edytować ten plik, aby określić domyślny przełączniki wiersza polecenia do MSBuild.exe. Na przykład, jeśli używasz tego samego rejestrowania za każdym razem, gdy tworzysz projekt, można dodać **/logger** Przełącz się do MSBuild.rsp i MSBuild.exe użyje rejestratora za każdym razem, gdy projekt jest kompilowany.  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do narzędzia MSBuild](../msbuild/msbuild-reference.md)   
 [Dokumentacja wiersza polecenia](../msbuild/msbuild-command-line-reference.md)
