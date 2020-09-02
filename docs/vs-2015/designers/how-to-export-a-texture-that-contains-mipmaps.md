---
title: 'Instrukcje: eksportowanie tekstury zawierającej mipmapy | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: 3d1ad14b-44fb-4cf0-a995-5e2f60026524
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 55418f40f57e2279100fbb1c9ba4d12fae83a19c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72664443"
---
# <a name="how-to-export-a-texture-that-contains-mipmaps"></a>Porady: eksportowanie tekstury zawierającej mipmapy
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Potok zawartości obrazu może generować mipmapy z obrazu źródłowego jako część fazy kompilacji projektu. Gdy nie musisz określać ręcznie zawartości obrazu dla każdego poziomu MCI — tak jak można osiągnąć pewne efekty — generowanie mipmapy w czasie kompilacji gwarantuje, że zawartość mipmappingu nigdy nie stanie się synchronizowana i eliminuje koszt wydajności generowania mipmapy w czasie wykonywania.

 W tym dokumencie przedstawiono następujące działania:

- Konfigurowanie obrazu źródłowego, który ma być przetwarzany przez potok zawartości obrazu.

- Konfigurowanie potoku zawartości obrazu w celu wygenerowania mipmapy.

## <a name="exporting-mipmaps"></a>Eksportowanie mipmapy
 Mipmapping zapewnia Automatyczny poziom szczegółowości ekranu dla powierzchni teksturowanych w grze 3D lub aplikacji. Zwiększa to wydajność renderowania gry lub aplikacji przez wstępne obliczenie wersji tekstury z próbką w dół, dzięki czemu cała tekstura nie musi być próbkowana w dół przy każdej próbie.

#### <a name="to-export-a-texture-that-has-mipmaps"></a>Aby wyeksportować teksturę, która ma mipmapy

1. Zacznij od tekstury podstawowej. Załaduj istniejący plik obrazu lub utwórz go zgodnie z opisem w temacie [How to: Create a Basic Texture](../designers/how-to-create-a-basic-texture.md). Aby obsłużyć mipmapy, należy określić teksturę, która ma szerokość i wysokość, które są takie same jak te same wartości, na przykład 64x64, 256x256 lub 512 x 512.

2. Skonfiguruj utworzony plik tekstury w taki sposób, aby był przetwarzany przez potok zawartości obrazu. W **Eksplorator rozwiązań**Otwórz menu skrótów dla właśnie utworzonego pliku tekstury, a następnie wybierz polecenie **Właściwości**. Na stronie **Właściwości konfiguracji**, **Ogólne** ustaw właściwość **Typ elementu** na **potok zawartości obrazu**. Upewnij się, że właściwość **Content** jest ustawiona na **wartość Yes (tak** ), **Wyklucz z kompilacji** jest ustawiony na **nie**, a następnie wybierz przycisk **Zastosuj** . Zostanie wyświetlona strona właściwości konfiguracja **potoku zawartości obrazu** .

3. Skonfiguruj potok zawartości obrazu w celu wygenerowania mipmapy. Na stronie **Właściwości konfiguracji**, **potoku zawartości obrazu**, **Ogólne** ustaw właściwość Generuj wartość właściwości **MIPS** na **wartość tak (/generatemips)**.

4. Wybierz przycisk **OK** .

   Podczas kompilowania projektu potok zawartości obrazów konwertuje obraz źródłowy z formatu roboczego do formatu wyjściowego, który określono, włącznie z poziomami MIP, a wynik jest kopiowany do katalogu wyjściowego projektu.
