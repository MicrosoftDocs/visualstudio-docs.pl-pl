---
title: 'Porady: eksportowanie tekstury wykorzystującej wstępnie przemnożony kanał alfa'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 05348afa-f079-4f53-a05b-ecd91d13adab
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 84017bef80f42bd1848833b957abd88297d1e12d
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "72635484"
---
# <a name="how-to-export-a-texture-that-has-premultiplied-alpha"></a>Instrukcje: eksportowanie tekstury wykorzystującej wstępnie przemnożony kanał alfa

Potok zawartości obrazu może generować wstępniemulowane tekstury alfa z obrazu źródłowego. Mogą one być prostsze w użyciu i bardziej niezawodne niż tekstury, które nie zawierają wstępnie wstępnie zamroczone alfa.

W tym dokumencie przedstawiono następujące działania:

- Konfigurowanie obrazu źródłowego do przetworzenia przez potok zawartości obrazu.

- Konfigurowanie potoku zawartości obrazu do generowania wstępniemultiplied alfa.

## <a name="premultiplied-alpha"></a>Wstępnie zmiksowana alfa
Wstępnie z góry skostniała alfa oferuje kilka zalet w stosunku do konwencjonalnej, niewmulowanej alfa, ponieważ lepiej reprezentuje rzeczywistą interakcję światła z materiałami fizycznymi poprzez oddzielenie wkładu koloru texel (kolor, który dodaje do scena) z jego przezroczystości (ilość koloru bazowego, który pozwala przez). Oto niektóre z zalet używania wstępniemultiplied alfa:

- Mieszanie z wstępniemultiplied alfa jest operacją asoprocyjną; wynik mieszania wielu przezroczystych tekstur jest taki sam, niezależnie od kolejności mieszania tekstur.

- Ze względu na asocenacyjny charakter mieszania z wstępniemultiplied alfa, wieloprzebiegowe renderowanie obiektów przezroczystych jest uproszczone.

- Za pomocą wstępniemultiplied alfa, zarówno czystego dodatku mieszania (przez ustawienie alfa do zera) i liniowo interpolowane mieszania można osiągnąć jednocześnie. Na przykład w systemie cząstek, addytywnie zmieszane cząstki ognia mogą stać się półprzezroczystą cząstką dymu, która jest mieszana za pomocą interpolacji liniowej. Bez wstępniemultiplied alfa, trzeba by wyciągnąć cząstki ognia oddzielnie od cząstek dymu i zmodyfikować stan renderowania między wywołaniami rysowania.

- Tekstury, które używają wstępnie sprężonych alfa kompresu o wyższej jakości niż te, które tego nie robią, i nie wykazują przebarwień krawędzi lub "efektu halo", które mogą powodować mieszanie tekstur, które nie używają wstępnie przemęczonej alfa.

#### <a name="to-create-a-texture-that-uses-premultiplied-alpha"></a>Aby utworzyć teksturę, która używa wstępniemultiplied alfa

1. Zacznij od podstawowej tekstury. Załaduj istniejący plik obrazu lub utwórz go w sposób opisany w [aplikacji Jak: Tworzenie tekstury podstawowej](../designers/how-to-create-a-basic-texture.md).

2. Skonfiguruj plik tekstury tak, aby był przetwarzany przez potok zawartości obrazu. W **Eksploratorze rozwiązań**otwórz menu skrótów dla pliku tekstury, a następnie wybierz polecenie **Właściwości**. Na stronie **Właściwości konfiguracji** > **ogólne** ustaw właściwość Typ **elementu** na Potok **zawartości obrazu**. Upewnij się, że właściwość **Content** jest ustawiona na **Tak,** a **opcja Wyklucz z kompilacji** jest ustawiona na **Nie**, a następnie wybierz przycisk **Zastosuj.** Zostanie wyświetlona strona właściwości właściwości konfiguracji **potoku zawartości** obrazu.

3. Skonfiguruj potok zawartości obrazu do generowania wstępniemultiplied alfa. Na stronie**Ogólne**  > **potoku** > zawartości obrazu właściwości **Właściwości Konwertuj**na **wstępnie pomnożone w formacie alfa** na **Tak (/generatepremultipliedalpha)**.

4. Wybierz przycisk **OK.**

   Podczas tworzenia projektu potok zawartości obrazu konwertuje obraz źródłowy z formatu roboczego na określony format wyjściowy — obejmuje to konwersję obrazu na wstępnie zwymierowany format alfa — a wynik jest kopiowany do danych wyjściowych projektu Katalogu.