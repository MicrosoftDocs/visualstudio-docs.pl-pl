---
title: 'CA1725: nazwy parametrów powinny być zgodne z deklaracją podstawową | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- ParameterNamesShouldMatchBaseDeclaration
- CA1725
helpviewer_keywords:
- CA1725
- ParameterNamesShouldMatchBaseDeclaration
ms.assetid: 9b657ab0-fe81-4f4c-9481-ba746988c922
caps.latest.revision: 13
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: f1fb30cd37ebffcee7619190cef83560813b25db
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85547371"
---
# <a name="ca1725-parameter-names-should-match-base-declaration"></a>CA1725: Nazwy parametrów powinny być zgodne z deklaracją podstawową
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|Wartość|
|-|-|
|TypeName|ParameterNamesShouldMatchBaseDeclaration|
|CheckId|CA1725|
|Kategoria|Microsoft. nazewnictwo|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
 Nazwa parametru w niewidocznym na zewnątrz przesłonięciu metody nie pasuje do nazwy parametru w podstawowej deklaracji metody lub nazwy parametru w deklaracji interfejsu metody.

## <a name="rule-description"></a>Opis reguły
 Spójne nazywanie parametrów w zastąpieniu hierarchii zwiększa użyteczność zastąpienia metody. Jeśli nazwa parametru w metodzie pochodnej różni się od nazwy podstawowej deklaracji, może nie być jasne, czy metoda jest zastąpieniem metody podstawowej, czy też nowym przeciążeniem metody.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej reguły, Zmień nazwę parametru tak, aby była zgodna z deklaracją podstawową. Poprawka jest istotną zmianą dla metod widocznych dla modelu COM.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżenia z tej reguły, z wyjątkiem metod widocznych dla modelu COM w bibliotekach, które zostały wcześniej dostarczone.
