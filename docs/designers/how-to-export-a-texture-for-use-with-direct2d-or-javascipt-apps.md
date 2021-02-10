---
title: Eksportowanie tekstury dla aplikacji Direct2D i JavaScript
description: Potok zawartości obrazu generuje tekstury zgodne z renderowaniem wewnętrznym Direct2D do użycia w aplikacjach Direct2D i platformy UWP aplikacjach utworzonych przy użyciu języka JavaScript.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 241c25fe-764e-4e1b-ad32-b1377dcbb605
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 84fadd786e7a1bf978ec4df919b691031c316a4a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99930957"
---
# <a name="how-to-export-a-texture-for-use-with-direct2d-or-javascript-apps"></a>Instrukcje: eksportowanie tekstury do użycia z aplikacjami Direct2D lub JavaScript

Potok zawartości obrazu może generować tekstury zgodne z wewnętrznymi konwencjami renderowania Direct2D's. Tekstury tego rodzaju są odpowiednie do użycia w aplikacjach korzystających z Direct2D, a w aplikacjach platformy UWP utworzonych przy użyciu języka JavaScript.

W tym dokumencie przedstawiono następujące działania:

- Konfigurowanie obrazu źródłowego, który ma być przetwarzany przez potok zawartości obrazu.

- Konfigurowanie potoku zawartości obrazu w celu wygenerowania tekstury, która może być używana w aplikacji Direct2D lub JavaScript.

  - Generowanie skompresowanego bloku pliku *. DDS* .

  - Generuj wstępnie przemnożony kanał alfa.

  - Wyłącz generowanie mipmappingu.

## <a name="rendering-conventions-in-direct2d"></a>Konwencje renderowania w Direct2D

Tekstury, które są używane w kontekście Direct2D, muszą być zgodne z tymi wewnętrznymi konwencjami renderowania Direct2D:

- Direct2D implementuje przezroczystość i przezroczystości przy użyciu wstępnie przemnożonego kanału alfa. Tekstury używane z Direct2D muszą zawierać wstępnie przemnożony kanał alfa, nawet jeśli tekstura nie używa przezroczystości ani przezroczystości. Aby uzyskać więcej informacji na temat wstępnie przemnożonego kanału alfa, zobacz [How to: Export a Texture z wstępnie przemnożoną alfa](../designers/how-to-export-a-texture-that-has-premultiplied-alpha.md).

- Tekstura musi być podana w formacie *. DDS* przy użyciu jednego z następujących formatów kompresji bloków:

  - Kompresja BC1_UNORM

  - Kompresja BC2_UNORM

  - Kompresja BC3_UNORM

- Mipmapy nie są obsługiwane.

### <a name="to-create-a-texture-thats-compatible-with-direct2d-rendering-conventions"></a>Aby utworzyć teksturę zgodną z konwencjami renderowania Direct2D

1. Zacznij od tekstury podstawowej. Załaduj istniejący obraz lub Utwórz nowy, zgodnie z opisem w temacie [How to: Create a Basic Texture](../designers/how-to-create-a-basic-texture.md). Aby zapewnić obsługę kompresji blokowej w formacie *. DDS* , należy określić teksturę, która ma szerokość i wysokość, które są wielokrotnościami czterech, na przykład 100x100, 128 x 128 lub 256x192. Ponieważ mipmapping nie jest obsługiwana, tekstura nie musi być kwadratowa i nie musi być potęgą liczby dwa.

2. Skonfiguruj plik tekstury w taki sposób, aby był przetwarzany przez potok zawartości obrazu. W **Eksplorator rozwiązań** Otwórz menu skrótów dla właśnie utworzonego pliku tekstury, a następnie wybierz polecenie **Właściwości**. Na stronie **Ogólne właściwości konfiguracji**  >   ustaw właściwość **Typ elementu** na **potok zawartości obrazu**. Upewnij się, że właściwość **Content** jest ustawiona na **wartość Yes (tak** ), **Wyklucz z kompilacji** jest ustawiony na **nie**, a następnie wybierz przycisk **Zastosuj** . Zostanie wyświetlona strona właściwości konfiguracja **potoku zawartości obrazu** .

3. Ustaw format danych wyjściowych na jeden z formatów skompresowanych blokowo. Na   >  stronie Ogólne **potoku zawartości obrazu** właściwości konfiguracji  >   ustaw właściwość **Kompresuj** na **BC3_UNORM kompresję (/Compress: BC3_UNORM)**. W zależności od wymagań można wybrać dowolny z innych formatów BC1, BC2 lub BC3. Direct2D obecnie nie obsługuje tekstur BC4, BC5, BC6 lub BC7. Aby uzyskać więcej informacji o różnych formatach BC, zobacz [kompresja bloków (Direct3D 10)](/windows/desktop/direct3d10/d3d10-graphics-programming-guide-resources-block-compression).

   > [!NOTE]
   > Określony format kompresji określa format pliku, który jest tworzony przez potok zawartości obrazu. Jest to inna niż Właściwość **Format** obrazu źródłowego w edytorze obrazów, która określa format pliku obrazu źródłowego jako przechowywanego na dysku — czyli *formatu roboczego*. Zwykle nie chcesz, aby format roboczy był skompresowany.

4. Skonfiguruj potok zawartości obrazu, aby utworzyć dane wyjściowe korzystające z wstępnie przemnożonego kanału alfa. Na   >  stronie Ogólne **potoku zawartości obrazu** właściwości konfiguracji  >   ustaw właściwość **Konwertuj na wstępnie przemnożony format alfa** na **wartość tak (/generatepremultipliedalpha)**.

5. Skonfiguruj potok zawartości obrazu, tak aby nie generował mipmapy. Na   >  stronie Ogólne **potoku zawartości obrazu** właściwości konfiguracji  >   ustaw wartość **nie** w polu Generuj Właściwość **MIPS** .

6. Wybierz przycisk **OK** .

   Podczas kompilowania projektu potok zawartości obrazów konwertuje obraz źródłowy z formatu roboczego do formatu wyjściowego, który określiłeś — konwersja obejmuje generowanie wstępnie przemnożonego kanału alfa, a wynik jest kopiowany do katalogu wyjściowego projektu.
