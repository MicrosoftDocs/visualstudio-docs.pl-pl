---
title: Różne, XML, Edytor tekstu, Opcje — okno dialogowe | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: fd3fff31-cddc-422d-a2f0-a5a1ef492afd
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: d30564c11951d6ffec420c6a2ea95c41695de3dd
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72656234"
---
# <a name="miscellaneous-xml-text-editor-options-dialog-box"></a>Inne, XML, Edytor tekstu, Opcje, okno dialogowe
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

To okno dialogowe umożliwia zmianę ustawień autouzupełniania i schematu dla edytora XML. Dostęp do okna dialogowego **Opcje** można uzyskać z menu **Narzędzia** .

> [!NOTE]
> Te ustawienia są dostępne po wybraniu folderu **Edytor tekstu** , folderu **XML** , a następnie opcji **różne** z okna dialogowego **Opcje** .

## <a name="auto-insert"></a>Autowstawianie
 **Zamknij Tagi** Jeśli ustawienie autouzupełniania jest zaznaczone, Edytor automatycznie dodaje tag końcowy po wpisaniu prawego nawiasu ostrego (>), aby zamknąć tag początkowy, jeśli tag nie jest już zamknięty. Jest to zachowanie domyślne.

 Zakończenie pustego elementu nie zależy od ustawienia autouzupełniania. Można zawsze Autouzupełnianie pustego elementu przez wpisanie ukośnika odwrotnego (/).

 **Cudzysłowy atrybutów** Podczas tworzenia atrybutów XML edytor wstawia `=" "` znaki i umieszcza karetkę (^) wewnątrz podwójnych cudzysłowów.

 Wybrane domyślnie.

 **Deklaracje przestrzeni nazw** Edytor automatycznie wstawia deklaracje przestrzeni nazw wszędzie tam, gdzie są one zbędne.

 Wybrane domyślnie.

 **Inne znaczniki (komentarze, CDATA)** Komentarze, CDATA, DOCTYPE, instrukcje przetwarzania i inne znaczniki są wypełniane pomyślnie.

 Wybrane domyślnie.

## <a name="network"></a>Sieć
 **Automatycznie pobieraj definicje DTD i schematy** Schematy i definicje typu dokumentu (DTD) są automatycznie pobierane z lokalizacji HTTP. Ta funkcja korzysta z System.Net z włączoną funkcją automatycznego wykrywania serwera proxy.

 Wybrane domyślnie.

## <a name="outlining"></a>Tworzenie konspektu
 **Wejdź do trybu konspektu przy otwieraniu plików** Włącza funkcję tworzenia konspektu, gdy plik zostanie otwarty.

 Wybrane domyślnie.

## <a name="caching"></a>Buforowanie
 **Schematy** Określa lokalizację pamięci podręcznej schematu. Przycisk przeglądania ( **...** ) otwiera okno dialogowe **Przeglądanie katalogów** w bieżącej lokalizacji pamięci podręcznej schematu. Możesz wybrać inny katalog lub wybrać folder w oknie dialogowym, kliknij prawym przyciskiem myszy i wybierz polecenie **Otwórz** , aby zobaczyć, co znajduje się w katalogu.

## <a name="see-also"></a>Zobacz też
 [Właściwości dokumentu XML,](../xml-tools/xml-document-properties-properties-window.md) [Składniki edytora XML](../xml-tools/xml-editor-components.md) okna właściwości
