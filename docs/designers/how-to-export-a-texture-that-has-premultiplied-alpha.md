---
title: 'Porady: eksportowanie tekstury wykorzystującej wstępnie przemnożony kanał alfa'
description: Dowiedz się, jak potok zawartości obrazu generuje wstępnie przemnożone tekstury alfa z obrazu źródłowego, który może być łatwiejszy do użycia i bardziej niezawodny.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 05348afa-f079-4f53-a05b-ecd91d13adab
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 56e8d198e55b521b761f8f3a7b54f6c2c0ee2c33
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99930941"
---
# <a name="how-to-export-a-texture-that-has-premultiplied-alpha"></a>Instrukcje: eksportowanie tekstury wykorzystującej wstępnie przemnożony kanał alfa

Potok zawartości obrazu może generować wstępnie przemnożone tekstury alfa z obrazu źródłowego. Te funkcje mogą być prostsze i bardziej niezawodne niż tekstury, które nie zawierają wstępnie przemnożonego kanału alfa.

W tym dokumencie przedstawiono następujące działania:

- Konfigurowanie obrazu źródłowego, który ma być przetwarzany przez potok zawartości obrazu.

- Konfigurowanie potoku zawartości obrazu w celu wygenerowania wstępnie przemnożonego kanału alfa.

## <a name="premultiplied-alpha"></a>Wstępnie przemnożone alfa
Wstępnie przemnożony kanał alfa oferuje kilka korzyści w porównaniu do konwencjonalnych, niewstępnie przemnożonych alfa, ponieważ lepiej reprezentuje rzeczywistą interakcję z materiałami fizycznymi, oddzielając Texel od koloru (kolor, który został dodany do sceny) od jego przezroczystości (ilość koloru bazowego, który umożliwia). Niektóre zalety korzystania z wstępnie przemnożonego kanału alfa są następujące:

- Mieszanie ze wstępnie przemnożonym alfa jest operacją asocjacyjną; wynik mieszania wielu przezroczystych tekstur jest taki sam, niezależnie od kolejności, w jakiej tekstury są mieszane.

- Ze względu na asocjacyjny charakter mieszania przy użyciu wstępnie przemnożonego kanału alfa jest uproszczone renderowanie wielu przebiegów przezroczystych obiektów.

- Za pomocą wstępnie przemnożonego kanału alfa, zarówno czysta mieszanie addytywne (poprzez ustawienie alfa na zero), jak i liniowo interpolowane mieszanie można osiągnąć jednocześnie. Na przykład w systemie cząsteczek, dostosowana mieszanina ognia może stać się przezroczystą cząstką dym, która jest zmieszana przy użyciu interpolacji liniowej. Bez wstępnie przemnożonego kanału alfa należy narysować cząstki pożarowe niezależnie od cząstek dymu i zmodyfikować stan renderowania między wywołaniami rysowania.

- Tekstury używające wstępnie przemnożonej kompresji alfa o wyższej jakości niż te, które nie są i nie wykazują odbarwnych krawędzi — lub "efektu otoczki", które mogą wynikać z mieszania tekstur, które nie używają wstępnie przemnożonego kanału alfa.

#### <a name="to-create-a-texture-that-uses-premultiplied-alpha"></a>Aby utworzyć teksturę, która używa wstępnie przemnożonego kanału alfa

1. Zacznij od tekstury podstawowej. Załaduj istniejący plik obrazu lub utwórz go zgodnie z opisem w temacie [How to: Create a Basic Texture](../designers/how-to-create-a-basic-texture.md).

2. Skonfiguruj plik tekstury w taki sposób, aby był przetwarzany przez potok zawartości obrazu. W **Eksplorator rozwiązań** Otwórz menu skrótów dla pliku tekstury, a następnie wybierz polecenie **Właściwości**. Na stronie **Ogólne właściwości konfiguracji**  >   ustaw właściwość **Typ elementu** na **potok zawartości obrazu**. Upewnij się, że właściwość **Content** jest ustawiona na **wartość Yes (tak** ), **Wyklucz z kompilacji** jest ustawiony na **nie**, a następnie wybierz przycisk **Zastosuj** . Zostanie wyświetlona strona właściwości konfiguracja **potoku zawartości obrazu** .

3. Skonfiguruj potok zawartości obrazu w celu wygenerowania wstępnie przemnożonego kanału alfa. Na   >  stronie Ogólne **potoku zawartości obrazu** właściwości konfiguracji  >   ustaw właściwość **Konwertuj na wstępnie przemnożony format alfa** na **wartość tak (/generatepremultipliedalpha)**.

4. Wybierz przycisk **OK** .

   Podczas kompilowania projektu potok zawartości obrazów konwertuje obraz źródłowy z formatu roboczego do formatu wyjściowego, który określiłeś — obejmuje to konwersję obrazu na wstępnie przemnożony format alfa, a wynik jest kopiowany do katalogu wyjściowego projektu.