---
title: 'Instrukcje: Tworzenie i modyfikacja poziomów MIP | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: f64d4369-2307-4175-a39a-2e45506f7fa1
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 6495f9271114be5fcd35e38d9ed210e07a8b6f66
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54774065"
---
# <a name="how-to-create-and-modify-mip-levels"></a>Instrukcje: Tworzenie i modyfikacja poziomów MIP
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W tym dokumencie przedstawiono sposób użycia **edytora obrazów** do generowania i modyfikowania *poziomów MIP* dla przestrzeni tekstury poziomu z Detail (poziomu).  
  
## <a name="generating-mip-levels"></a>Generowanie poziomów MIP  
 *Mipmapping* to technika, który jest używany do zwiększenia szybkości renderowania i zmniejszania artefaktów wygładzania na obiektach z teksturą przez wstępne Obliczanie i przechowywania kilku kopii tekstury różnych rozmiarów. Każda kopia, która jest znany jako poziom minimalnej ceny Importowej, jest połowę szerokości i wysokości poprzedniej kopii. Po wyrenderowaniu tekstury na powierzchni obiektu poziom MIP, który najlepiej odpowiada obszarowi miejsca na ekranie powierzchni teksturowanej, jest automatycznie wybierany. Oznacza to, że sprzęt graficzny nie musi odfiltrowywać zbyt dużych tekstur, aby utrzymać spójną jakość wizualną. Chociaż koszt pamięci przy przechowywaniu poziomów MIP jest około 33% wyższy niż samej oryginalnej tekstury, wydajności i jakości obrazu zyski uzasadnić ją.  
  
#### <a name="to-generate-mip-levels"></a>Aby wygenerować poziomy MIP  
  
1.  Rozpocznij od podstawowej tekstury, zgodnie z opisem w [jak: Tworzenie tekstury podstawowej](../designers/how-to-create-a-basic-texture.md). Aby uzyskać najlepsze wyniki, należy określić teksturę, która ma szerokość i wysokość, które są wartością potęgi liczby dwa, na przykład 256, 512, 1024 itd.  
  
2.  Generuj poziomy MIP. Na **tryb edytora obrazów** narzędzi, wybierz **zaawansowane**, **narzędzia**, **Generuj Mips**.  
  
     Należy zauważyć, że **przejdź do następnego poziomu Mip** i **przejdź do poprzedniego poziomu Mip** przyciski będą teraz wyświetlane na **tryb edytora obrazów** paska narzędzi. Jeśli **właściwości** okno jest wyświetlane, należy również zauważyć, że właściwości tylko do odczytu **poziom Mip** i **liczba poziomów Mip** pojawiają się w oknie właściwości obrazu.  
  
## <a name="modifying-mip-levels"></a>Modyfikowanie poziomów MIP  
 Aby uzyskać efekty specjalne lub zwiększyć jakość obrazu na określonym poziomie szczegółowości, można zmodyfikować indywidualnie każdy poziom MIP. Na przykład obiektowi z teksturą można nadać inny wygląd w odległości (większa odległość odpowiada mniejszym poziomom MIP) lub można zapewnić, że tekstury, które zawierają tekst lub symbole, pozostaną czytelne nawet na mniejszych poziomach MIP.  
  
#### <a name="to-modify-an-individual-mip-level"></a>Aby zmodyfikować jeden poziom MCI  
  
1.  Zaznacz poziom MIP, który chcesz zmodyfikować. Na **tryb edytora obrazów** narzędzi, użyj **przejdź do następnego poziomu MIP** i **przejdź do poprzedniego poziomu MIP** przycisków, aby przenieść między poziomami MIP.  
  
2.  Po wybraniu poziom MIP, który chcesz zmodyfikować, można użyć narzędzi do rysowania go zmodyfikować bez zmiany zawartości innych poziomów MCI. Narzędzia do rysowania są dostępne na **edytora obrazów** paska narzędzi. Po wybraniu narzędzia, możesz zmienić jego właściwości w **właściwości** okna. Aby uzyskać informacji na temat narzędzi do rysowania i ich właściwości, zobacz [edytora obrazów](../designers/image-editor.md).  
  
> [!NOTE]
>  Jeśli nie trzeba modyfikować zawartość poszczególnych poziomów MIP — co możesz zrobić, aby uzyskać pewne efekty — firma Microsoft zaleca generowanie mipmap z tekstury źródłowej w czasie kompilacji. Pomaga to zapewnić, że poziomy MCI pozostają zsynchronizowane z teksturą źródła, ponieważ modyfikacje poziomu MIP nie są propagowane do innych poziomów automatycznie. Aby uzyskać więcej informacji na temat generowania mipmap w czasie kompilacji, zobacz [jak: Eksportowanie tekstury zawierającej mipmapy](../designers/how-to-export-a-texture-that-contains-mipmaps.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Instrukcje: Tworzenie tekstury podstawowej](../designers/how-to-create-a-basic-texture.md)
