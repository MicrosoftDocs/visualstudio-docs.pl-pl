---
title: 'Porady: eksportowanie tekstury zawierającej mipmapy'
description: Dowiedz się, jak potok zawartości obrazu generuje mipmapy z obrazu źródłowego w ramach kompilowania projektu, co gwarantuje, że mipmapy nigdy nie przestanie być zsynchronizowany.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 3d1ad14b-44fb-4cf0-a995-5e2f60026524
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 783f8935b5d9eee25d6569dea9ba48b0eaeae8bd
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99930939"
---
# <a name="how-to-export-a-texture-that-contains-mipmaps"></a>Instrukcje: eksportowanie tekstury zawierającej mipmapy

Potok zawartości obrazu może generować mipmapy z obrazu źródłowego jako część fazy kompilacji projektu. Aby osiągnąć pewne skutki, czasami trzeba ręcznie określić zawartość obrazu dla każdego poziomu MCI. Gdy nie musisz określać ręcznie zawartości obrazu dla każdego poziomu MIP, generowanie mipmapy w czasie kompilacji zapewnia, że zawartość mipmappingu nigdy nie będzie zsynchronizowana. Eliminuje także koszt wydajności generowania mipmapy w czasie wykonywania.

W tym artykule omówiono następujące zagadnienia:

- Konfigurowanie obrazu źródłowego, który ma być przetwarzany przez potok zawartości obrazu.

- Konfigurowanie potoku zawartości obrazu w celu wygenerowania mipmapy.

## <a name="export-mipmaps"></a>Eksportuj mipmapy

Mipmapping zapewnia Automatyczny poziom szczegółowości ekranu dla powierzchni teksturowanych w grze 3D lub aplikacji. Zwiększa to wydajność renderowania gry lub aplikacji przez wstępne obliczenie wersji tekstury z próbką w dół. Wstępne obliczanie wersji z próbką w dół oznacza, że cała tekstura nie musi być próbkowana w dół przy każdej próbie.

### <a name="to-export-a-texture-that-has-mipmaps"></a>Aby wyeksportować teksturę, która ma mipmapy

1. Zacznij od tekstury podstawowej. Załaduj istniejący plik obrazu lub utwórz go zgodnie z opisem w temacie [How to: Create a Basic Texture](../designers/how-to-create-a-basic-texture.md). Aby obsłużyć mipmapy, należy określić teksturę, która ma szerokość i wysokość, które są takie same jak te same wartości, na przykład 64x64, 256x256 lub 512 x 512.

2. Skonfiguruj utworzony plik tekstury w taki sposób, aby był przetwarzany przez potok zawartości obrazu. W **Eksplorator rozwiązań** Otwórz menu skrótów dla utworzonego pliku tekstury, a następnie wybierz polecenie **Właściwości**. Na stronie **Ogólne właściwości konfiguracji**  >   ustaw właściwość **Typ elementu** na **potok zawartości obrazu**. Upewnij się, że właściwość **Content** jest ustawiona na **wartość Yes (tak** ), a wartość **exclude z kompilacji** to **no**. Wybierz przycisk **Zastosuj**.

   Zostanie wyświetlona strona właściwości konfiguracja **potoku zawartości obrazu** .

3. Skonfiguruj potok zawartości obrazu w celu wygenerowania mipmapy. Na   >  stronie Ogólne **potoku zawartości obrazu** właściwości konfiguracji  >   ustaw właściwość **Generuj MIPS** na **wartość tak (/generatemips)**.

4. Wybierz przycisk **OK**.

Podczas kompilowania projektu potok zawartości obrazów konwertuje obraz źródłowy z formatu roboczego do formatu wyjściowego, który określiłeś, włącznie z poziomami MIP. Wynik jest kopiowany do katalogu wyjściowego projektu.
