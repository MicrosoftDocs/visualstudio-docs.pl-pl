---
title: 'Instrukcje: Ustawienie atrybutów CLR w elemencie | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
f1_keywords:
- vs.dsltools.EditAttributesDialog
helpviewer_keywords:
- Domain-Specific Language, custom attrributes
ms.assetid: b3db3c74-920c-4701-9544-6f75cbe8b7c9
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 576b9a6890a6a6de398e917c1c152dcdb2f3ef16
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54804338"
---
# <a name="how-to-set-clr-attributes-on-an-element"></a>Instrukcje: Ustawienie atrybutów CLR w elemencie
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Atrybuty niestandardowe są specjalne atrybuty, które mogą być dodawane do elementy domeny, kształty, łączników i diagramy. Możesz dodać dowolny atrybut, który dziedziczy z `System.Attribute` klasy.  
  
### <a name="to-add-a-custom-attribute"></a>Aby dodać atrybut niestandardowy  
  
1.  W **Eksplorator DSL**, wybierz element, do którego chcesz dodać atrybut niestandardowy.  
  
2.  W **właściwości** okna, obok **atrybuty niestandardowe** właściwości, kliknij przycisk Przeglądaj (**...** ) ikona.  
  
     **Edycja atrybutów** zostanie otwarte okno dialogowe.  
  
3.  W **nazwa** kolumny, kliknij przycisk  **\<Dodaj atrybut >** i wpisz nazwę swojej atrybutu. Naciśnij klawisz ENTER.  
  
4.  Wiersz pod nazwą atrybutu zawiera nawiasy. W tym wierszu typu parametru atrybutu (na przykład `string`), a następnie naciśnij klawisz ENTER.  
  
5.  W **właściwości Name** kolumny, wpisz odpowiednią nazwę, na przykład `MyString`.  
  
6.  Kliknij przycisk **OK**.  
  
     **Atrybuty niestandardowe** właściwości wyświetla teraz atrybutu w następującym formacie:  
  
     `[` *AttributeName* `(` *ParameterName* `=` *typu* `)]`  
  
## <a name="see-also"></a>Zobacz też  
 [Słownik narzędzi języka specyficznego dla domeny](http://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
