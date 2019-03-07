---
title: schematy XML
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.xmleditor.schemasdialog
ms.assetid: 0271fa26-2205-49bd-96e0-ae1441571808
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f5323582bfe945bc031b9fd02fcf96bb615bcceb
ms.sourcegitcommit: 3ca33862c1cfc3ccb83de3e95f1e69e860ab143a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57524926"
---
# <a name="xml-schemas-dialog-box"></a>Okno dialogowe schematy XML

**Schematów XML** okno dialogowe służy do wybierania które schematy XML schematu definicji języka (XSD) do skojarzenia z dokumentu XML. Wybierz schemat z pamięci podręcznej schematów lub określ schemat, który nie znajduje się w pamięci podręcznej. Wybrane schematy są traktowane jako część zestawu schematu. Zestaw schematu jest używany dla funkcji IntelliSense, a także Walidacja dokumentów XML.

Możesz uzyskać dostęp **schematów XML** okno dialogowe, albo klikając **schematów** przycisku w oknie dialogowym właściwości dokumentu lub wybierając **schematów** z **XML** menu.

## <a name="uielement-list"></a>Lista elementów UI

**Korzystanie**

Wybierz, jak ma być używany schemat XML.

- **Automatyczne**. W tym schemacie nie jest używany przez bieżącego dokumentu, ale są dostępne na automatyczne kojarzenie. Jeśli dokument XML deklaruje przestrzeni nazw, który odpowiada `targetNamespace` tego schematu schemat zostaną automatycznie skojarzone i znajduje się w zestawie schematów.

- **Użyj tego schematu**. Ten schemat jest on używany przez bieżącego dokumentu. Użytkownik ma jawnie zażądano, można użyć tego schematu, klikając tę kolumnę lub schemat został automatycznie skojarzone w oparciu o dopasowanie `targetNamespace`.

- **Nie używaj wybranych schematów**. W tym schemacie nie jest używany przez bieżącego dokumentu, nawet wtedy, gdy schemat miała zgodną `targetNamespace`. To ustawienie może być przydatne w przypadku rozwiązywania konfliktów, jeśli istnieje więcej niż jedna wersja ten sam schemat w pamięci podręcznej schematów lub rozwiązania.

**TARGET Namespace**

Wyświetla docelowego obszaru nazw, skojarzone ze schematem XML.

**Nazwa pliku**

Wyświetla nazwę pliku schematu XML.

**Add**

Otwiera **otwieranie schematu XSD** okno dialogowe, które umożliwia wybranie dodatkowe schematy do dodania do zestawu schematów. Po dodaniu schematu do schematu ustawiony **użyj** jest równa wartości w kolumnie **używają tego schematu**.

**Usuń**

Usuwa aktualnie wybranego schematu z zestawu schematów. Spowoduje to usunięcie schematu z pamięci podręcznej schematów w pamięci, ale nie z systemu plików.

## <a name="see-also"></a>Zobacz także

- [Instrukcje: Wybieranie schematów XML do użycia](../xml-tools/how-to-select-the-xml-schemas-to-use.md)
- [Pamięci podręcznej schematów](../xml-tools/schema-cache.md)