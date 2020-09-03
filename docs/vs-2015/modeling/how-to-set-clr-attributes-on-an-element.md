---
title: 'Instrukcje: ustawianie atrybutów CLR dla elementu | Microsoft Docs'
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 72ad9175729451c82fca3b61d06e449edaf8cf38
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72662540"
---
# <a name="how-to-set-clr-attributes-on-an-element"></a>Porady: ustawienie atrybutów CLR w elemencie
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Atrybuty niestandardowe są specjalnymi atrybutami, które mogą być dodawane do elementów domeny, kształtów, łączników i diagramów. Można dodać dowolny atrybut, który dziedziczy z `System.Attribute` klasy.

### <a name="to-add-a-custom-attribute"></a>Aby dodać atrybut niestandardowy

1. W **Eksploratorze DSL**wybierz element, do którego chcesz dodać atrybut niestandardowy.

2. W oknie **Właściwości** obok właściwości **atrybuty niestandardowe** kliknij ikonę Przeglądaj (**...**).

     Zostanie otwarte okno dialogowe **Edytowanie atrybutów** .

3. W kolumnie **Nazwa** kliknij **\<add attribute>** i wpisz nazwę atrybutu. Naciśnij klawisz ENTER.

4. Wiersz pod nazwą atrybutu zawiera nawiasy. W tym wierszu wpisz typ parametru dla atrybutu (na przykład `string` ), a następnie naciśnij klawisz ENTER.

5. W kolumnie **Nazwa właściwości** wpisz odpowiednią nazwę, na przykład `MyString` .

6. Kliknij przycisk **OK**.

     Właściwość **atrybuty niestandardowe** wyświetla teraz atrybut w następującym formacie:

     `[`*AttributeName* `(` *Parametrname* `=` *Typ*`)]`

## <a name="see-also"></a>Zobacz też
 [narzędzia języka specyficznego dla domeny słownik](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
