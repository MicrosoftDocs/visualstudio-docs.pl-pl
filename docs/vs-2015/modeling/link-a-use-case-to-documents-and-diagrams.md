---
title: Łączenie przypadku użycia z dokumentami i diagramami | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
f1_keywords:
- vs.teamarch.usecasediagram.artifact.properties.artifactlink
- vs.teamarch.usecasediagram.artifact
helpviewer_keywords:
- use case diagrams
ms.assetid: 4c9ed205-9197-4ed5-b39d-ddfa24a0a421
caps.latest.revision: 12
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c713759a8ea75eed3048469327f962668efa4f70
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72657638"
---
# <a name="link-a-use-case-to-documents-and-diagrams"></a>Łączenie przypadków użycia z dokumentami i diagramami
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Możesz połączyć przypadek użycia w diagramie przypadku użycia z innym diagramem lub dokumentem. Można na przykład połączyć przypadek użycia z następującymi diagramami i dokumentami:

- Diagram sekwencji pokazujący, jak cele przypadku użycia są realizowane przez interakcje między użytkownikami a systemem lub jego głównym składnikiem.

- Diagram aktywności, który pokazuje szczegółowe działania użytkowników i system lub jego główne składniki, gdy wykonują przypadki użycia.

- Strona lub akapit programu OneNote, w którym szczegółowo opisano przypadek użycia.

- Dokument programu Word lub prezentację programu PowerPoint opisującą przypadek użycia szczegółowo. Można zachować takie dokumenty w rozwiązaniu lub w lokalizacji dostępnej dla zespołu, na przykład w witrynie programu SharePoint.

  Aby połączyć przypadek użycia z dokumentem, należy utworzyć artefakt na diagramie przypadków użycia i połączyć przypadek użycia z artefaktem. We właściwościach artefaktu ustawiasz ścieżkę pliku dla innego diagramu lub dokumentu. Po dwukrotnym kliknięciu artefaktu zostanie otwarty inny diagram lub dokument.

  Możesz połączyć dowolną liczbę artefaktów z każdym przypadkiem użycia. Można również łączyć artefakty z innymi rodzajami elementów na diagramie przypadków użycia.

### <a name="to-open-a-document-associated-with-an-artifact"></a>Aby otworzyć dokument skojarzony z artefaktem

- Na diagramie przypadku użycia kliknij dwukrotnie kształt artefaktu.

     Zostanie otwarty skojarzony dokument.

### <a name="to-link-a-use-case-to-a-diagram-or-file-in-the-same-solution"></a>Aby połączyć przypadek użycia z diagramem lub plikiem w tym samym rozwiązaniu

1. Narysuj diagram, taki jak diagram sekwencji lub diagram aktywności, aby zilustrować scenariusz przypadków użycia.

2. Wróć do diagramu przypadków użycia.

3. Przeciągnij diagram lub plik z Eksplorator rozwiązań na pustą część diagramu przypadków użycia.

4. Nawiąż połączenie z artefaktu z przypadkiem użycia przy użyciu **zależności**.

### <a name="to-link-to-a-solution-file-such-as-a-word-document-or-powerpoint-presentation"></a>Aby utworzyć link do pliku rozwiązania, takiego jak dokument programu Word lub prezentacja programu PowerPoint

1. Dodaj dokument do rozwiązania.

    1. Przenieś dokument programu Word do tego samego folderu systemu Windows, w którym znajduje się rozwiązanie.

    2. W Eksplorator rozwiązań kliknij prawym przyciskiem myszy rozwiązanie, wskaż polecenie **Dodaj**, a następnie kliknij pozycję **istniejący element**.

    3. Przejdź do dokumentu programu Word i kliknij przycisk **Dodaj**.

         Dokument programu Word zostanie wyświetlony w folderze rozwiązania w Eksplorator rozwiązań.

2. Przeciągnij dokument programu Word z Eksplorator rozwiązań na pustą część diagramu przypadków użycia.

     Zostanie wyświetlony nowy artefakt.

3. Nawiąż połączenie z artefaktu z przypadkiem użycia przy użyciu **zależności**.

### <a name="to-link-to-a-shared-document-onenote-element-or-web-page"></a>Aby połączyć się z dokumentem udostępnionym, elementem programu OneNote lub stroną sieci Web

1. Uzyskaj adres URL elementu udostępnionego. Może to być na przykład ścieżką pliku sieciowego rozpoczynającą się "\\ \\" lub stronę sieci Web lub adres URL programu SharePoint, zaczynając od "http://" lub link do sekcji programu OneNote, strony lub akapitu rozpoczynającego się "OneNote:".

2. W przyborniku kliknij pozycję **artefakt** , a następnie kliknij pozycję na diagramie przypadku użycia.

3. Po wybraniu nowego artefaktu wpisz lub wklej adres URL do właściwości **Hyperlink** .

    > [!NOTE]
    > Jeśli chcesz podać ścieżkę pliku, najlepiej wybrać plik w wspólnym obszarze roboczym (rozpoczynając od "\\ \\") lub pliku w rozwiązaniu programu Visual Studio. Gwarantuje to, że ścieżka pliku pozostanie prawidłowa na komputerze z innym członkiem zespołu lub jeśli rozwiązanie zostanie przeniesione. Aby dodać do rozwiązania dokument, taki jak dokument programu Word, kliknij prawym przyciskiem myszy rozwiązanie w Eksplorator rozwiązań, wskaż polecenie **Dodaj** , a następnie kliknij pozycję **istniejący element**.

## <a name="see-also"></a>Zobacz też
 [Diagramy przypadków użycia UML: referencyjne](../modeling/uml-use-case-diagrams-reference.md) [diagramy przypadków użycia UML: wytyczne](../modeling/uml-use-case-diagrams-guidelines.md) [Edytowanie modeli UML i diagramów](../modeling/edit-uml-models-and-diagrams.md) [Tworzenie modeli dla aplikacji](../modeling/create-models-for-your-app.md)
