---
title: 'Instrukcje: Eksportowanie tekstury zawierającej mipmapy'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 3d1ad14b-44fb-4cf0-a995-5e2f60026524
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f5226903112d06d5efa362c61db938124eed8e68
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55919251"
---
# <a name="how-to-export-a-texture-that-contains-mipmaps"></a>Instrukcje: Eksportowanie tekstury zawierającej mipmapy

Potok zawartości obrazu może generować mipmapy z obrazu źródłowego w ramach fazy kompilacji projektu. Aby uzyskać pewne efekty, czasami trzeba ręcznie określać zawartości obrazu każdego poziomu MIP. Gdy nie trzeba ręcznie określać zawartości obrazu każdego poziomu MIP, generowanie mipmap w czasie kompilacji zapewnia, że zawartość mipmappingu nigdy nie stanie się poza synchronizacji. Eliminuje koszty wydajności wytwarzania mipmap w czasie wykonywania.

W tym artykule omówiono:

- Konfigurowanie obrazu źródłowego, który ma być przetwarzana przez potok zawartości obrazu.

- Konfigurowanie potoku zawartości obrazu, aby nie generować mipmap.

## <a name="export-mipmaps"></a>Eksportowanie mipmap

Mipmapping zapewnia automatyczne ekranowego poziom szczegółów wypełniający dla teksturowanych powierzchni w grze lub aplikacji 3D. Zwiększa wydajność renderowania gry lub aplikacji poprzez wstępnie obliczenie wersji tekstury. Wstępne przetwarzanie próbkowana w dół wersjami oznacza, że cały Tekstura nie musiała być próbkowana w dół każdorazowo go próbkowania.

### <a name="to-export-a-texture-that-has-mipmaps"></a>Aby wyeksportować teksturę, która ma mipmapy

1. Rozpocznij od podstawowej tekstury. Załaduj istniejący pliku obrazu lub utwórz je, zgodnie z opisem w [jak: Tworzenie tekstury podstawowej](../designers/how-to-create-a-basic-texture.md). Aby obsługiwać mipmapy, określ teksturę, która ma szerokość i wysokość, które są tego samego przekazu dwa, na przykład 64 x 64, 256 x 256 lub 512 x 512.

2. Skonfigurować pliku tekstury, który został utworzony, aby jest przetwarzany przez potok zawartości obrazu. W **Eksploratora rozwiązań**, otwórz menu skrótów dla pliku tekstury, został utworzony, a następnie wybierz **właściwości**. Na **właściwości konfiguracji** > **ogólne** ustaw **typu elementu** właściwości **potok zawartości obrazu**. Upewnij się, że **zawartości** właściwość jest ustawiona na **tak** i **Wyłącz z kompilacji** ustawiono **nie**. Wybierz przycisk **Zastosuj**.

   **Potok zawartości obrazu** zostanie wyświetlona strona właściwości konfiguracji.

3. Konfigurowanie potoku zawartości obrazu, aby nie generować mipmap. Na **właściwości konfiguracji** > **potok zawartości obrazu** > **ogólne** ustaw **Generuj Mips** właściwości **tak (/ generatemips)**.

4. Kliknij przycisk **OK**.

Podczas budowania projektu potok zawartości obrazów konwertuje obraz źródłowy z formatu roboczego do formatu wyjściowego, który określiłeś, włącznie z poziomami MIP. Wynik jest kopiowany do katalogu wyjściowego projektu.