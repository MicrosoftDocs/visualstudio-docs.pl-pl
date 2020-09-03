---
title: Warunki MSBuild | Microsoft Docs
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
- MSBuild, conditions
- conditions [MSBuild]
ms.assetid: 9d7aa308-b667-48ed-b4c9-a61e49eb0a85
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 71bb48290d0eb64f91b918d22624755c2edb6153
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "74303126"
---
# <a name="msbuild-conditions"></a>Warunki MSBuild
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] obsługuje określony zestaw warunków, które mogą być stosowane wszędzie tam, gdzie `Condition` atrybut jest dozwolony. W poniższej tabeli opisano te warunki.  
  
|Warunek|Opis|  
|---------------|-----------------|  
|'`stringA`' == '`stringB`'|Zwraca wartość, `true` Jeśli `stringA` jest równa `stringB` .<br /><br /> Na przykład:<br /><br /> `Condition="'$(CONFIG)'=='DEBUG'"`<br /><br /> Pojedyncze cudzysłowy nie są wymagane w przypadku prostych ciągów alfanumerycznych lub wartości logicznych. Jednak dla pustych wartości są wymagane pojedyncze cudzysłowy.|  
|'`stringA`' != '`stringB`'|Daje w `true` przypadku, gdy `stringA` nie jest równe `stringB` .<br /><br /> Na przykład:<br /><br /> `Condition="'$(CONFIG)'!='DEBUG'"`<br /><br /> Pojedyncze cudzysłowy nie są wymagane w przypadku prostych ciągów alfanumerycznych lub wartości logicznych. Jednak dla pustych wartości są wymagane pojedyncze cudzysłowy.|  
|\<, >, \<=, >=|Oblicza wartości liczbowe argumentów operacji. Zwraca `true` czy wartość oceny relacyjnej to true. Operandy muszą mieć wartość dziesiętną lub szesnastkową. Liczby szesnastkowe muszą zaczynać się od ciągu "0x". **Uwaga:**  W formacie XML, znaki `<` i `>` muszą być zmienione. Symbol `<` jest reprezentowany jako `<` . Symbol `>` jest reprezentowany jako `>` .|  
|Istnieje (' `stringA` ')|Zwraca wartość, `true` Jeśli istnieje plik lub folder o nazwie `stringA` .<br /><br /> Na przykład:<br /><br /> `Condition="!Exists('$(builtdir)')"`<br /><br /> Pojedyncze cudzysłowy nie są wymagane w przypadku prostych ciągów alfanumerycznych lub wartości logicznych. Jednak dla pustych wartości są wymagane pojedyncze cudzysłowy.|  
|HasTrailingSlash (' `stringA` ')|Zwraca wartość `true` , jeśli określony ciąg zawiera znak ukośnika odwrotnego ( \\ ) lub ukośnika (/).<br /><br /> Na przykład:<br /><br /> `Condition="!HasTrailingSlash('$(OutputPath)')"`<br /><br /> Pojedyncze cudzysłowy nie są wymagane w przypadku prostych ciągów alfanumerycznych lub wartości logicznych. Jednak dla pustych wartości są wymagane pojedyncze cudzysłowy.|  
|!|Daje w `true` przypadku, gdy operand zwraca wartość `false` .|  
|And|Zwraca wartość, `true` Jeśli oba operandy są oceniane do `true` .|  
|Lub|Zwraca wartość, `true` Jeśli co najmniej jeden z operandów ma wartość `true` .|  
|()|Mechanizm grupowania, który jest obliczany w `true` wyrażeniach if zawartych w obliczaniu do `true` .|  
|$if $ (% Expression%), $else $, $endif $|Sprawdza, czy określony `%expression%` pasuje do wartości ciągu podanego parametru szablonu niestandardowego. Jeśli `$if$` warunek ma wartość `true` , instrukcje są uruchamiane; w przeciwnym razie `$else$` warunek jest zaznaczony. Jeśli `$else$` warunek ma wartość `true` , instrukcje są uruchamiane; w przeciwnym razie warunek spowoduje `$endif$` zakończenie obliczania wyrażenia.<br /><br /> Przykłady użycia można znaleźć w temacie [logika parametrów projektu/elementu programu Visual Studio](https://stackoverflow.com/questions/6709057/visual-studio-project-item-template-parameter-logic).|  
  
## <a name="see-also"></a>Zobacz też  
 [Dokumentacja programu MSBuild](../msbuild/msbuild-reference.md)   
 [Konstrukcje warunkowe](../msbuild/msbuild-conditional-constructs.md)   
 [Przewodnik: Tworzenie pliku projektu MSBuild od podstaw](../msbuild/walkthrough-creating-an-msbuild-project-file-from-scratch.md)
