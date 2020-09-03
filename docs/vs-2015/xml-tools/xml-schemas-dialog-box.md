---
title: Okno dialogowe schematy XML | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 0271fa26-2205-49bd-96e0-ae1441571808
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: d637cb3c25772685d5a782eb74bf94878ded36c2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72669424"
---
# <a name="xml-schemas-dialog-box"></a>Schematy XML, okno dialogowe
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Okno dialogowe **schematy XML** służy do wybierania schematu definicji języka (XSD) XML do skojarzenia z dokumentem XML. Można wybrać schemat z pamięci podręcznej schematów lub określić schemat, który nie znajduje się w pamięci podręcznej. Wybrane schematy są uważane za część zestawu schematów. Zestaw schematu jest używany na potrzeby funkcji IntelliSense, a także do sprawdzania poprawności dokumentu XML.

 Możesz uzyskać dostęp do okna dialogowego **schematy XML** , klikając przycisk **schematy** w oknie właściwości dokumentu lub wybierając **schematy** z menu **XML** .

## <a name="uielement-list"></a>Lista elementów UI
 **Użyj** Wybierz, jak schemat XML ma być używany.

- **Automatyczne**. Ten schemat nie jest używany przez bieżący dokument, ale jest dostępny do automatycznego kojarzenia. Jeśli dokument XML deklaruje przestrzeń nazw zgodną `targetNamespace` z tym schematem, schemat zostanie automatycznie skojarzony i zostanie uwzględniony w zestawie schematów.

- **Użyj tego schematu**. Ten schemat jest używany przez bieżący dokument. Użytkownik jawnie zażądał użycia tego schematu przez kliknięcie tej kolumny lub schemat został automatycznie skojarzony na podstawie pasującego elementu `targetNamespace` .

- **Nie używaj wybranych schematów**. Ten schemat nie jest używany przez bieżący dokument, nawet jeśli schemat ma pasujący element `targetNamespace` . To ustawienie może być przydatne do rozwiązywania konfliktów, jeśli istnieje więcej niż jedna wersja tego samego schematu w pamięci podręcznej schematów lub w rozwiązaniu.

  **Docelowa przestrzeń nazw** Wyświetla docelową przestrzeń nazw skojarzoną ze schematem XML.

  **Nazwa pliku** Wyświetla nazwę pliku schematu XML.

  **Dodaj** Otwiera okno dialogowe **otwieranie schematu XSD** , które umożliwia wybranie dodatkowych schematów do dodania do zestawu schematów. Po dodaniu schematu do zestawu schematów wartość **opcji Użyj** kolumny jest ustawiana na **Użyj tego schematu**.

  **Usuń** Usuwa aktualnie wybrany schemat z zestawu schematów. Spowoduje to usunięcie schematu z pamięci podręcznej schematu w pamięci, ale nie z systemu plików.

## <a name="see-also"></a>Zobacz też
 [Składniki edytora XML](../xml-tools/xml-editor-components.md) [— instrukcje: Wybieranie schematów XML do użycia](../xml-tools/how-to-select-the-xml-schemas-to-use.md) [pamięci podręcznej schematu](../xml-tools/schema-cache.md)
