---
title: schematy XML
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.xmleditor.schemasdialog
ms.assetid: 0271fa26-2205-49bd-96e0-ae1441571808
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 11743756ffd8f59520448d2687dbada6d4eaca40
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72608037"
---
# <a name="xml-schemas-dialog-box"></a>Schematy XML, okno dialogowe

Okno dialogowe **schematy XML** służy do wybierania schematu definicji języka (XSD) XML do skojarzenia z dokumentem XML. Można wybrać schemat z pamięci podręcznej schematów lub określić schemat, który nie znajduje się w pamięci podręcznej. Wybrane schematy są uważane za część zestawu schematów. Zestaw schematu jest używany na potrzeby funkcji IntelliSense, a także do sprawdzania poprawności dokumentu XML.

Możesz uzyskać dostęp do okna dialogowego **schematy XML** , klikając przycisk **schematy** w oknie właściwości dokumentu lub wybierając **schematy** z menu **XML** .

## <a name="uielement-list"></a>Lista elementów UI

**Używanych**

Wybierz, jak schemat XML ma być używany.

- **Automatyczne**. Ten schemat nie jest używany przez bieżący dokument, ale jest dostępny do automatycznego kojarzenia. Jeśli dokument XML deklaruje przestrzeń nazw pasującą do `targetNamespace` tego schematu, schemat zostanie automatycznie skojarzony i zostanie uwzględniony w zestawie schematów.

- **Użyj tego schematu**. Ten schemat jest używany przez bieżący dokument. Użytkownik jawnie zażądał użycia tego schematu przez kliknięcie tej kolumny lub schemat został automatycznie skojarzony na podstawie pasującego `targetNamespace`.

- **Nie używaj wybranych schematów**. Ten schemat nie jest używany przez bieżący dokument, nawet jeśli schemat ma pasujące `targetNamespace`. To ustawienie może być przydatne do rozwiązywania konfliktów, jeśli istnieje więcej niż jedna wersja tego samego schematu w pamięci podręcznej schematów lub w rozwiązaniu.

**Docelowa przestrzeń nazw**

Wyświetla docelową przestrzeń nazw skojarzoną ze schematem XML.

**Nazwa pliku**

Wyświetla nazwę pliku schematu XML.

**Add**

Otwiera okno dialogowe **otwieranie schematu XSD** , które umożliwia wybranie dodatkowych schematów do dodania do zestawu schematów. Po dodaniu schematu do zestawu schematów wartość **opcji Użyj** kolumny jest ustawiana na **Użyj tego schematu**.

**Usuń**

Usuwa aktualnie wybrany schemat z zestawu schematów. Spowoduje to usunięcie schematu z pamięci podręcznej schematu w pamięci, ale nie z systemu plików.

## <a name="see-also"></a>Zobacz także

- [Instrukcje: Wybieranie schematów XML do użycia](../xml-tools/how-to-select-the-xml-schemas-to-use.md)
- [Pamięć podręczna schematu](../xml-tools/schema-cache.md)