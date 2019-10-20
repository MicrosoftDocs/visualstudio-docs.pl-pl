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
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72635484"
---
# <a name="how-to-export-a-texture-that-has-premultiplied-alpha"></a>Instrukcje: eksportowanie tekstury z wstępnie przemnożoną alfa

Potok zawartości obrazu może generować wstępnie przemnożone tekstury alfa z obrazu źródłowego. Te funkcje mogą być prostsze i bardziej niezawodne niż tekstury, które nie zawierają wstępnie przemnożonego kanału alfa.

W tym dokumencie przedstawiono następujące działania:

- Konfigurowanie obrazu źródłowego, który ma być przetwarzany przez potok zawartości obrazu.

- Konfigurowanie potoku zawartości obrazu w celu wygenerowania wstępnie przemnożonego kanału alfa.

## <a name="premultiplied-alpha"></a>Wstępnie przemnożone alfa
Wstępnie przemnożone alfa daje kilka korzyści w porównaniu do konwencjonalnych, niewstępnie przemnożonych alfa, ponieważ lepiej reprezentuje rzeczywistą interakcję światła z materiałami fizycznymi, oddzielając Texel od koloru (kolor dodany do scena) z jej przezroczystości (ilość koloru bazowego, którą umożliwia za pośrednictwem). Niektóre zalety korzystania z wstępnie przemnożonego kanału alfa są następujące:

- Mieszanie ze wstępnie przemnożonym alfa jest operacją asocjacyjną; wynik mieszania wielu przezroczystych tekstur jest taki sam, niezależnie od kolejności, w jakiej tekstury są mieszane.

- Ze względu na asocjacyjny charakter mieszania przy użyciu wstępnie przemnożonego kanału alfa jest uproszczone renderowanie wielu przebiegów przezroczystych obiektów.

- Za pomocą wstępnie przemnożonego kanału alfa, zarówno czysta mieszanie addytywne (poprzez ustawienie alfa na zero), jak i liniowo interpolowane mieszanie można osiągnąć jednocześnie. Na przykład w systemie cząsteczek, dostosowana mieszanina ognia może stać się przezroczystą cząstką dym, która jest zmieszana przy użyciu interpolacji liniowej. Bez wstępnie przemnożonego kanału alfa należy narysować cząstki pożarowe niezależnie od cząstek dymu i zmodyfikować stan renderowania między wywołaniami rysowania.

- Tekstury używające wstępnie przemnożonej kompresji alfa o wyższej jakości niż te, które nie są i nie wykazują odbarwnych krawędzi — lub "efektu otoczki", które mogą wynikać z mieszania tekstur, które nie używają wstępnie przemnożonego kanału alfa.

#### <a name="to-create-a-texture-that-uses-premultiplied-alpha"></a>Aby utworzyć teksturę, która używa wstępnie przemnożonego kanału alfa

1. Zacznij od tekstury podstawowej. Załaduj istniejący plik obrazu lub utwórz go zgodnie z opisem w temacie [How to: Create a Basic Texture](../designers/how-to-create-a-basic-texture.md).

2. Skonfiguruj plik tekstury w taki sposób, aby był przetwarzany przez potok zawartości obrazu. W **Eksplorator rozwiązań**Otwórz menu skrótów dla pliku tekstury, a następnie wybierz polecenie **Właściwości**. Na stronie**Ogólne** **Właściwości**  >  ustaw właściwość **Typ elementu** na **potok zawartości obrazu**. Upewnij się, że właściwość **Content** jest ustawiona na **wartość Yes (tak** ), **Wyklucz z kompilacji** jest ustawiony na **nie**, a następnie wybierz przycisk **Zastosuj** . Zostanie wyświetlona strona właściwości konfiguracja **potoku zawartości obrazu** .

3. Skonfiguruj potok zawartości obrazu w celu wygenerowania wstępnie przemnożonego kanału alfa. Na stronie **Właściwości konfiguracji**  > **potoku zawartości obrazu**  > **Ogólne** ustaw właściwość **Konwertuj na wstępnie przemnożony format alfa** na **wartość tak (/generatepremultipliedalpha)** .

4. Wybierz przycisk **OK** .

   Podczas kompilowania projektu potok zawartości obrazów konwertuje obraz źródłowy z formatu roboczego do formatu wyjściowego, który określiłeś — obejmuje to konwersję obrazu na wstępnie przemnożony format alfa — a wynik jest kopiowany do danych wyjściowych projektu katalogi.