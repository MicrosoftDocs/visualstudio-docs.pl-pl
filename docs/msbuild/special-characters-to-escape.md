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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ca7df1c087e35fd188461382e4f44de6ab703964
ms.sourcegitcommit: 16175e0cea6af528e9ec76f0b94690faaf1bed30
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/28/2019
ms.locfileid: "71481958"
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
|).|Nawias zamykający używany na listach.|
|;|Średnik, separator listy.|
|?|Znak zapytania, symbol wieloznaczny podczas opisywania specyfikacji pliku w sekcji dołączania/wykluczania elementu.|
|*|Gwiazdka, symbol wieloznaczny podczas opisywania specyfikacji pliku w sekcji dołączania/wykluczania elementu.|

> [!NOTE]
> W niektórych scenariuszach może zajść potrzeba ucieczki znaków podwójnego cudzysłowu ("), na przykład podczas korzystania z zadania `Exec`.

## <a name="see-also"></a>Zobacz także
- [Instrukcje: znaki specjalne ucieczki w MSBuild](../msbuild/how-to-escape-special-characters-in-msbuild.md)
- [Dokumentacja programu MSBuild](../msbuild/msbuild-reference.md)
