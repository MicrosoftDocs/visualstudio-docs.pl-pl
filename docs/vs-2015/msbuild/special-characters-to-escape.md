---
title: Znaki specjalne do ucieczki | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- special characters to escape
- msbuild, special characters to escape
ms.assetid: 5b5172c3-41e4-4f38-a16f-2aeac831a5fc
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: beeed84db240ecf57ca18dd9aef08622f14b06fc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68161355"
---
# <a name="special-characters-to-escape"></a>Znaki specjalne wyjścia
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Znaki specjalne muszą być wyprowadzane tylko wtedy, gdy mają specjalne znaczenie w kontekście, w którym są używane. Na przykład gwiazdka (*) jest znakiem specjalnym tylko w atrybutach "include" i "exclude" definicji elementu lub w wywołaniu <xref:Microsoft.Build.Tasks.CreateItem> . We wszystkich innych przypadkach gwiazdka jest traktowana jako literał gwiazdki. Mimo że nie ma potrzeby ucieczki gwiazdek w plikach projektu, nie jest to szkodliwe.  
  
 Użyj notacji%*XX* zamiast znaku specjalnego, gdzie *XX* reprezentuje wartość szesnastkową znaku ASCII. Na przykład, aby użyć gwiazdki (*) jako znaku literału, użyj wartości `%2A` .  
  
 Pełna lista znaków specjalnych do wyjścia w następujący sposób:  
  
|Znak|Opis|  
|---------------|-----------------|  
|%|Znak procentu używany do odwoływania się do metadanych.|  
|$|Znak dolara używany do odwoływania się do właściwości.|  
|@|Znak używany do odwoływania się do list elementów.|  
|(|Otwórz nawias, używany na listach.|  
|)|Nawias zamykający używany na listach.|  
|`|Apostrof (lub znacznik) używany w warunkach i innych wyrażeniach.|  
|;|Średnik, separator listy.|  
|?|Znak zapytania, symbol wieloznaczny podczas opisywania specyfikacji pliku w sekcji dołączania/wykluczania elementu.|  
|*|Gwiazdka, symbol wieloznaczny podczas opisywania specyfikacji pliku w sekcji dołączania/wykluczania elementu.|  
  
## <a name="see-also"></a>Zobacz też  
 [Instrukcje: znaki specjalne ucieczki w MSBuild](../msbuild/how-to-escape-special-characters-in-msbuild.md)   
 [Dokumentacja programu MSBuild](../msbuild/msbuild-reference.md)
