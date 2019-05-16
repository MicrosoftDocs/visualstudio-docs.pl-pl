---
title: 'Instrukcje: Eksportowanie tekstury do użycia z Direct2D lub aplikacjami JavaScript | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: 241c25fe-764e-4e1b-ad32-b1377dcbb605
caps.latest.revision: 13
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 98b08fc8ebf2fca207d41b644032d7abbcd97a24
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65681739"
---
# <a name="how-to-export-a-texture-for-use-with-direct2d-or-javascipt-apps"></a>Instrukcje: Eksportowanie tekstury do użycia z Direct2D lub aplikacjami JavaScript
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Potok zawartości obrazu może generować tekstury, które są zgodne z konwencjami renderowania wewnętrznego w Direct2D. Tekstury tego rodzaju są odpowiednie do użycia w aplikacjach, które używają Direct2D oraz w aplikacjach Windows Store utworzone przy użyciu języka JavaScript.  
  
 Ten dokument przedstawia te działania:  
  
- Konfigurowanie obrazu źródłowego, który ma być przetwarzana przez potok zawartości obrazu.  
  
- Konfigurowanie potoku zawartości obrazu do generowania tekstury, którego można używać w aplikacji Direct2D lub JavaScript.  
  
    - Generowanie pliku .DDS ze skompresowanym bloku.  
  
    - Generowanie wstępnie przemnożonego kanału alfa.  
  
    - Wyłącz Generowanie mipmappingu.  
  
## <a name="rendering-conventions-in-direct2d"></a>Konwencje renderowania w Direct2D  
 Tekstury, które są używane w kontekście Direct2D muszą spełniać te wewnętrzne konwencje renderowania Direct2D:  
  
- Direct2D implementuje przezroczystość przy użyciu wstępnie przemnożonego kanału alfa. Tekstury używane z Direct2D musi zawierać wstępnie przemnożony kanał alfa, nawet jeśli Tekstura nie używa przezroczystości ani przejrzystości. Aby uzyskać więcej informacji dotyczących wstępnie przemnożonego kanału alfa, zobacz [jak: Eksportowanie tekstury wykorzystującej wstępnie przemnożony kanał alfa](../designers/how-to-export-a-texture-that-has-premultiplied-alpha.md).  
  
- Tekstury muszą być dostarczane w formacie .dds, przy użyciu jednej z tych formatów kompresji blokowej:  
  
    - Kompresja bc1_unorm  
  
    - Kompresja bc2_unorm  
  
    - Kompresja bc3_unorm  
  
- Mipmapy nie są obsługiwane.  
  
#### <a name="to-create-a-texture-thats-compatible-with-direct2d-rendering-conventions"></a>Aby utworzyć teksturę, która jest zgodna z konwencjami renderowania Direct2D  
  
1. Rozpocznij od podstawowej tekstury. Załaduj istniejący obraz lub Utwórz nową, zgodnie z opisem w [jak: Tworzenie tekstury podstawowej](../designers/how-to-create-a-basic-texture.md). Do obsługi kompresji bloku w formacie .dds, należy określić teksturę, która ma szerokość i wysokość będące wielokrotnościami czterech, na przykład 100 x 100, 128 x 128 lub 256 x 192. Mipmapping nie jest obsługiwane, Tekstura nie musi mieć kształtu kwadratu i nie musi być potęgą liczby dwa.  
  
2. Skonfigurować pliku tekstury, jest przetwarzany przez potok zawartości obrazu. W **Eksploratora rozwiązań**, otwórz menu skrótów dla utworzonego właśnie pliku tekstury, a następnie wybierz **właściwości**. Na **właściwości konfiguracji**, **ogólne** ustaw **typu elementu** właściwości **potok zawartości obrazu**. Upewnij się, że **zawartości** właściwość jest ustawiona na **tak** i **Wyłącz z kompilacji** ustawiono **nie**, a następnie wybierz  **Zastosuj** przycisku. **Potok zawartości obrazu** zostanie wyświetlona strona właściwości konfiguracji.  
  
3. Ustaw format wyjściowy na jeden z formatów skompresowanego bloku. Na **właściwości konfiguracji**, **potok zawartości obrazu**, **ogólne** ustaw **skompresować** właściwości  **Kompresja bc3_unorm (/ compress: BC3_UNORM)**. Możesz wybrać dowolny z innych formantów BC1, BC2 lub BC3 formatów w zależności od wymagań. Direct2D nie obsługuje obecnie tekstur BC4, BC5, BC6 lub BC7 tekstury. Aby uzyskać więcej informacji o różnych formatach kompresji Blokowej, zobacz [kompresja blokowa (Direct3D 10)](https://msdn.microsoft.com/library/windows/desktop/bb694531.aspx).  
  
   > [!NOTE]
   > Format kompresji, który jest określony, określa format pliku, który jest wytwarzany przez potok zawartości obrazu. Stanowi to odmianę **Format** właściwości obrazu źródłowego w edytorze obrazu, który określa format pliku obrazu źródłowego, ponieważ przechowywane na dysku — czyli *formatu roboczego*. Nie ma zazwyczaj format roboczy był skompresowany.  
  
4. Konfigurowanie potoku zawartości obrazu do generowania danych wyjściowych, która używa wstępnie przemnożonego kanału alfa. Na **właściwości konfiguracji**, **potok zawartości obrazu**, **ogólne** ustaw **przekonwertować wstępnie przemnożonego alfa format** Właściwość **tak (/ generatepremultipliedalpha)**.  
  
5. Konfigurowanie potoku zawartości obrazu tak, aby nie generować mipmap. Na **właściwości konfiguracji**, **potok zawartości obrazu**, **ogólne** ustaw **Generuj Mips** właściwość **Nie**.  
  
6. Wybierz **OK** przycisku.  
  
   Podczas budowania projektu potok zawartości obrazów konwertuje obraz źródłowy z formatu roboczego do formatu wyjściowego, który określiłeś, konwersja obejmuje Generowanie wstępnie przemnożonego kanału alfa, a wynik jest kopiowany do katalogu wyjściowego projektu.
