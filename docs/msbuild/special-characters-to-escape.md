---
title: Znaki specjalne do ucieczki | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- special characters to escape
- msbuild, special characters to escape
ms.assetid: 5b5172c3-41e4-4f38-a16f-2aeac831a5fc
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d1b17ded468e262d4f636ed5494081adab7b8c5f
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/26/2020
ms.locfileid: "77632254"
---
# <a name="special-characters-to-escape"></a>Znaki specjalne do wyjścia

Znaki specjalne muszą być wyprowadzane tylko wtedy, gdy mają specjalne znaczenie w kontekście, w którym są używane. Na przykład gwiazdka (*) jest znakiem specjalnym tylko w atrybutach "include" i "exclude" definicji elementu lub w wywołaniu <xref:Microsoft.Build.Tasks.CreateItem>. We wszystkich innych przypadkach gwiazdka jest traktowana jako literał gwiazdki. Mimo że nie ma potrzeby ucieczki gwiazdek w plikach projektu, nie jest to szkodliwe.

 Użyj notacji%\<XX > zamiast znaku specjalnego, gdzie \<XX > reprezentuje wartość szesnastkową znaku ASCII. Na przykład, aby użyć gwiazdki (*) jako znaku literału, użyj wartości `%2A`.

 Pełna lista znaków specjalnych do wyjścia w następujący sposób:

|Znak|Opis|
|---------------|-----------------|
|%|Znak procentu używany do odwoływania się do metadanych.|
|$|Znak dolara używany do odwoływania się do właściwości.|
|@|Znak używany do odwoływania się do list elementów.|
|(|Otwórz nawias, używany na listach.|
|)|Nawias zamykający używany na listach.|
|;|Średnik, separator listy.|
|?|Znak zapytania, symbol wieloznaczny podczas opisywania specyfikacji pliku w sekcji dołączania/wykluczania elementu.|
|*|Gwiazdka, symbol wieloznaczny podczas opisywania specyfikacji pliku w sekcji dołączania/wykluczania elementu.|

> [!NOTE]
> W niektórych scenariuszach może zajść potrzeba ucieczki znaków podwójnego cudzysłowu ("), na przykład podczas korzystania z zadania `Exec`.

## <a name="see-also"></a>Zobacz też

- [Instrukcje: znaki specjalne ucieczki w MSBuild](../msbuild/how-to-escape-special-characters-in-msbuild.md)
- [Dokumentacja programu MSBuild](../msbuild/msbuild-reference.md)
