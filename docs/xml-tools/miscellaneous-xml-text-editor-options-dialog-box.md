---
title: Inne, XML, Edytor tekstu, Opcje, okno dialogowe
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
ms.assetid: fd3fff31-cddc-422d-a2f0-a5a1ef492afd
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 85af563d9fb20b12785a410cf7df7e612d17dbee
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53941404"
---
# <a name="miscellaneous-xml-text-editor-options-dialog-box"></a>Inne, XML, Edytor tekstu, okno dialogowe Opcje

To okno dialogowe umożliwia zmianę ustawień automatycznego uzupełniania i schematu edytora XML. Możesz uzyskać dostęp **opcje** okno dialogowe z **narzędzia** menu.

> [!NOTE]
> Te ustawienia są dostępne po wybraniu **edytora tekstów** folderze **XML** folder, a następnie **różne** opcję **opcje** okno dialogowe.


## <a name="auto-insert"></a>Automatyczne wstawianie
 **Zamknij tagów**

 Ustawienie automatycznego uzupełniania jest zaznaczone, Edytor automatycznie dodaje tag końcowy po wpisaniu nawiasu ostrego po prawej stronie (>), aby zamknąć tagu początkowego, jeśli tag nie jest już zamknięty. Jest to zachowanie domyślne.

 Ukończenie pusty element nie zależy od ustawienia automatycznego uzupełniania. Zawsze możesz autouzupełniania pustego elementu, wpisując kreska ułamkowa odwrócona (/).

 **Cudzysłowy atrybutu**

 Podczas tworzenia atrybutów XML, Edytor wstawia `=" "` znaków i umieszcza daszek (^) w podwójnym cudzysłowie.

 Domyślnie wybrana.

 **Deklaracji Namespace**

 Edytor automatycznie wstawi deklaracje przestrzeni nazw, wszędzie tam, gdzie jest to konieczne.

 Domyślnie wybrana.

 **Innych znaczników (komentarze, CDATA)**

 Komentarze, CDATA, elementu DOCTYPE, instrukcje przetwarzania i innych znaczników są automatycznie uzupełniane.

 Domyślnie wybrana.

## <a name="network"></a>Sieć
 **Automatycznie pobieraj definicje DTD i schematy**

 Schematy i definicji typu dokumentu (pliki DTD) są automatycznie pobierane z lokalizacji HTTP. Ta funkcja używa przestrzeni nazw System.Net z wykrywanie serwera proxy automatycznie włączone.

 Domyślnie wybrana.

## <a name="outlining"></a>Tworzenie konspektu
 **Przejdź do trybu konspektu po otwarciu plików**

 Włącza funkcję tworzenia konspektów podczas otwierania pliku.

 Domyślnie wybrana.

## <a name="caching"></a>Buforowanie
 **Schematy**

 Określa lokalizację pamięci podręcznej schematów. Przycisk przeglądania (**...** ) otwiera **Przeglądaj katalog** okno dialogowe w bieżącej lokalizacji pamięci podręcznej schematu. Możesz wybrać inny katalog, lub możesz wybrać folder, w oknie dialogowym kliknij prawym przyciskiem myszy, a wybierz **Otwórz** aby zobaczyć, co znajduje się w katalogu.

## <a name="see-also"></a>Zobacz także

- [Właściwości dokumentu XML, okno właściwości](../xml-tools/xml-document-properties-properties-window.md)
- [Składniki edytora XML](../xml-tools/xml-editor-components.md)