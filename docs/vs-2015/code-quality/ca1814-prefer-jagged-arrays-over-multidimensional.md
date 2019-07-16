---
title: 'CA1814: Preferuj Tablice nieregularne wielowymiarowych | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- PreferJaggedArraysOverMultidimensional
- CA1814
helpviewer_keywords:
- PreferJaggedArraysOverMultidimensional
- CA1814
ms.assetid: b1ccf563-2ec8-42e5-b89c-731a9de1ea1d
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 73b20ef9a93e59f3fae30407deda8d21befc57f5
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "68201700"
---
# <a name="ca1814-prefer-jagged-arrays-over-multidimensional"></a>CA1814: Wybieraj tablice nieregularne zamiast wielowymiarowych
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|PreferJaggedArraysOverMultidimensional|
|CheckId|CA1814|
|Kategoria|Microsoft.Performance|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
 Składowa jest zadeklarowana jako tablicę wielowymiarową.

## <a name="rule-description"></a>Opis reguły
 Nieregularna tablica to ta, której elementy są tablicami. Tablice, które tworzą elementy, mogą mieć różne rozmiary, co zapewnia większą oszczędność miejsca w przypadku niektórych zestawów danych.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej zasady, należy zmienić tablicy wielowymiarowej tablicy nieregularnej.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Pomijaj ostrzeżeń dla tej reguły, jeśli tablica wielowymiarowa nie traci miejsca.

## <a name="example"></a>Przykład
 Poniższy przykład pokazuje deklaracje dla nieregularnej i tablice wielowymiarowe.

 [!code-csharp[FxCop.Performance.JaggedArrays#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.JaggedArrays/cs/FxCop.Performance.JaggedArrays.cs#1)]
 [!code-vb[FxCop.Performance.JaggedArrays#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Performance.JaggedArrays/vb/FxCop.Performance.JaggedArrays.vb#1)]
