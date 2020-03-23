---
title: 'Porady: eksportowanie tekstury zawierającej mipmapy'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 3d1ad14b-44fb-4cf0-a995-5e2f60026524
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 71d570e6dc7544911ebe2bb279aafb3a07620cbc
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75589412"
---
# <a name="how-to-export-a-texture-that-contains-mipmaps"></a>Jak: Eksportowanie tekstury zawierającej mipmaps

Potok zawartości obrazu można wygenerować mipmaps z obrazu źródłowego w ramach fazy kompilacji projektu. Aby osiągnąć pewne efekty, czasami trzeba ręcznie określić zawartość obrazu każdego poziomu MIP. Jeśli nie trzeba ręcznie określić zawartość obrazu każdego poziomu MIP, generowanie mipmaps w czasie kompilacji zapewnia, że zawartość mipmap nigdy nie stają się niezsynchronizowane. Eliminuje również koszt wydajności generowania mipmaps w czasie wykonywania.

Ten artykuł obejmuje:

- Konfigurowanie obrazu źródłowego do przetworzenia przez potok zawartości obrazu.

- Konfigurowanie potoku zawartości obrazu do generowania mipmaps.

## <a name="export-mipmaps"></a>Eksportowanie mipmaps

Mipmapping zapewnia automatyczne poziom szczegółowości ekranu dla teksturowanych powierzchni w grze lub aplikacji 3D. Zwiększa wydajność renderowania gry lub aplikacji przez wstępne obliczanie wersji tekstury z próbką w dół. Wstępne obliczanie wersji próbkowanych w dół oznacza, że cała tekstura nie musi być próbkowana w dół za każdym razem, gdy jest próbkowana.

### <a name="to-export-a-texture-that-has-mipmaps"></a>Aby wyeksportować teksturę z mipmaps

1. Zacznij od podstawowej tekstury. Załaduj istniejący plik obrazu lub utwórz go w sposób opisany w [aplikacji Jak: Tworzenie tekstury podstawowej](../designers/how-to-create-a-basic-texture.md). Aby obsługiwać mipmaps, należy określić teksturę, która ma szerokość i wysokość, które mają taką samą moc dwóch rozmiarów, na przykład 64x64, 256x256 lub 512x512.

2. Skonfiguruj utworzony właśnie plik tekstury, tak aby był przetwarzany przez potok zawartości obrazu. W **Eksploratorze rozwiązań**otwórz menu skrótów dla utworzonego pliku tekstury, a następnie wybierz polecenie **Właściwości**. Na stronie **Właściwości konfiguracji** > **ogólne** ustaw właściwość Typ **elementu** na Potok **zawartości obrazu**. Upewnij się, że właściwość **Content** jest ustawiona na **Tak,** a **opcja Wyklucz z kompilacji** jest ustawiona na **Nie**. Wybierz przycisk **Zastosuj**.

   Zostanie wyświetlona strona właściwości właściwości konfiguracji **potoku zawartości** obrazu.

3. Skonfiguruj potok zawartości obrazu do generowania mipmaps. Na stronie**Ogólne** **potoku zawartości** > obrazu **właściwości konfiguracji** > ustaw właściwość **Generowanie mips** na **Tak (/generatemips).**

4. Kliknij przycisk **OK**.

Podczas tworzenia projektu potok zawartości obrazu konwertuje obraz źródłowy z formatu roboczego do formatu wyjściowego, który został określony, w tym poziomów MIP. Wynik jest kopiowany do katalogu wyjściowego projektu.
