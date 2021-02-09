---
title: Znaki specjalne do ucieczki | Microsoft Docs
description: Dowiedz się więcej na temat znaków specjalnych, które należy zmienić tylko wtedy, gdy mają specjalne znaczenie w kontekście, w którym są używane.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 5e665c214ea75de67a6c339bb516dfb812936448
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99878152"
---
# <a name="special-characters-to-escape"></a>Znaki specjalne, które należy poprzedzić znakiem ucieczki

Znaki specjalne muszą być wyprowadzane tylko wtedy, gdy mają specjalne znaczenie w kontekście, w którym są używane. Na przykład gwiazdka (*) jest znakiem specjalnym tylko w atrybutach "include" i "exclude" definicji elementu lub w wywołaniu <xref:Microsoft.Build.Tasks.CreateItem> . We wszystkich innych przypadkach gwiazdka jest traktowana jako literał gwiazdki. Mimo że nie ma potrzeby ucieczki gwiazdek w plikach projektu, nie jest to szkodliwe.

 Użyj zapisu% \<xx> zamiast znaku specjalnego, gdzie \<xx> reprezentuje wartość szesnastkową znaku ASCII. Na przykład, aby użyć gwiazdki (*) jako znaku literału, użyj wartości `%2A` .

 Pełna lista znaków specjalnych do wyjścia w następujący sposób:

|Znak|Kodowanie ASCII|Opis|
|---------|----------|-----------|
|%|%25|Znak procentu używany do odwoływania się do metadanych.|
|$|%24|Znak dolara używany do odwoływania się do właściwości.|
|@|%40|Znak używany do odwoływania się do list elementów.|
|(|%28|Otwórz nawias, używany na listach.|
|)|%29|Nawias zamykający używany na listach.|
|;|% 3B|Średnik, separator listy.|
|?|% 3F|Znak zapytania, symbol wieloznaczny podczas opisywania specyfikacji pliku w sekcji dołączania/wykluczania elementu.|
|* |%2A|Gwiazdka, symbol wieloznaczny podczas opisywania specyfikacji pliku w sekcji dołączania/wykluczania elementu.|

> [!NOTE]
> W niektórych scenariuszach może zajść potrzeba ucieczki znaków podwójnego cudzysłowu ("), na przykład podczas korzystania z `Exec` zadania.

## <a name="see-also"></a>Zobacz też

- [Instrukcje: znaki specjalne ucieczki w MSBuild](../msbuild/how-to-escape-special-characters-in-msbuild.md)
- [Dokumentacja programu MSBuild](../msbuild/msbuild-reference.md)
