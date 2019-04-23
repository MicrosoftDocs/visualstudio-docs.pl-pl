---
title: 'Instrukcje: Tworzenie cieniowania gradientu geometrycznego | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: 4b204405-ba95-4c5e-bd51-ec033a3ebfb6
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 8735931e761f7d511615b5be7e93e0198a6b1a45
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60071723"
---
# <a name="how-to-create-a-geometry-based-gradient-shader"></a>Instrukcje: Tworzenie cieniowania gradientu geometrycznego
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W tym dokumencie przedstawiono sposób umożliwia tworzenie cieniowania gradientu geometrycznego Shader Designer i język programu do cieniowania wykres kierowany. Ten program do cieniowania można skalować stałej wartości kolorów RGB przez wysokość każdego punktu obiektu w przestrzeni świata.  
  
 Ten dokument przedstawia te działania:  
  
- Dodawanie węzłów do wykresu programu do cieniowania  
  
- Ustawianie właściwości węzła  
  
- Trwa rozłączanie węzłów  
  
- Łączenie z węzłami  
  
## <a name="creating-a-geometry-based-gradient-shader"></a>Tworzenie cieniowania gradientu geometrycznego  
 Można zaimplementować programu do cieniowania geometrycznego, dołączając pozycja piksela do modułu cieniującego. W językach cieniowania pikseli zawiera więcej informacji, niż tylko jego kolor i położenie na ekranie 2-D. Piksel — znane jako *fragmentu* w niektórych systemach — jest to zbiór wartości, które opisują powierzchni, który odpowiada pikseli. Wysokość każdego piksela w przestrzeni świata wpływa na kolor ostatecznymi fragmentu obiektu 3-D korzysta z modułem cieniującym, który jest opisany w tym dokumencie.  
  
 Przed rozpoczęciem upewnij się, że **właściwości** okna i **przybornika** są wyświetlane.  
  
#### <a name="to-create-a-geometry-based-gradient-shader"></a>Aby utworzyć cieniowania gradientu geometrycznego  
  
1. Tworzenie modułu cieniującego DGSL chcesz pracować. Aby uzyskać informacje dotyczące sposobu dodawania modułu cieniującego DGSL do projektu, zobacz sekcję pierwsze kroki w [Shader Designer](../designers/shader-designer.md).  
  
2. Odłącz **koloru punktu** węzła z **ostateczny kolor** węzła. Wybierz **RGB** terminali z **koloru punktu** węzła, a następnie wybierz **Przerwij linki**. To sprawia, że miejsce na węzeł, który zostanie dodany do następnego kroku.  
  
3. Dodaj **mnożenia** węzła do wykresu. W **przybornika**w obszarze **matematyczne**, wybierz opcję **mnożenia** i przenieś go do powierzchni projektowej.  
  
4. Dodaj **wektor maski** węzła do wykresu. W **przybornika**w obszarze **narzędzie**, wybierz opcję **wektor maski** i przenieś go do powierzchni projektowej.  
  
5. Określ wartości maski **wektor maski** węzła. W **wybierz** tryb, wybierz **wektor maski** węzła, a następnie w polu **właściwości** oknie **zielony / Y** właściwość **Wartość true,**, a następnie ustaw **czerwony / X**, **niebieski / Z** i **alfa / W** właściwości w celu **False**. W tym przykładzie **czerwony / X**, **zielony / Y**, i **niebieski / Z** właściwości odpowiadają x, y i składniki z **pozycja świata** węzeł, i **alfa / W** jest nieużywana. Ponieważ tylko **zielony / Y** ustawiono **True**, tylko składnik y wektor wejściowy pozostaje po jego są wyświetlane jako znaki.  
  
6. Dodaj **pozycja świata** węzła do wykresu. W **przybornika**w obszarze **stałe**, wybierz opcję **pozycja świata** i przenieś go do powierzchni projektowej.  
  
7. Maski pozycji miejsca na świecie fragmentu. W **wybierz** tryb, Przenieś **dane wyjściowe** terminali z **pozycja świata** węzeł, aby **wektor** terminali z **maski Wektor** węzła. To połączenie maskuje pozycji fragmentu, aby zignorować x i z składników.  
  
8. Mnożenie — stała koloru RGB według pozycji miejsca na świecie maskowanego. Przenieś **RGB** terminali z **koloru punktu** węzeł, aby **Y** terminali z **mnożenia** węzeł, a następnie przenieść  **Dane wyjściowe** terminali z **wektor maski** węzeł **X** terminali z **mnożenia** węzła. To połączenie jest skalowana w wartości koloru, wysokość piksela w przestrzeni świata.  
  
9. Połącz się ostateczny kolor z wartości koloru skalowany. Przenieś **dane wyjściowe** terminali z **mnożenia** węzeł, aby **RGB** terminali z **ostateczny kolor** węzła.  
  
   Poniższej ilustracji ukończone programu do cieniowania programu graph i wersję zapoznawczą programu do cieniowania zastosowane do kuli.  
  
> [!NOTE]
>  Na tej ilustracji określono koloru pomarańczowego, aby lepiej pokazują wpływ programu do cieniowania, ale ponieważ kształtu (wersja zapoznawcza) nie ma żadnych pozycji w przestrzeni świata, programu do cieniowania nie pełni podglądu w projektancie programu do cieniowania. W rzeczywistych sceny w celu wykazania pełnego wpływu, można wyświetlić podglądu modułu cieniującego.  
  
 ![Wykres modułu cieniującego i podgląd efektów jej](../designers/media/digit-gradient-effect-graph.png "cyfry-gradientu — efekt-Graph")  
  
 Niektórych kształtów udostępniać lepsze wersje zapoznawcze niektórych programów do cieniowania. Aby dowiedzieć się, jak wyświetlić podgląd programów do cieniowania w projektancie programu do cieniowania, zobacz **Podgląd cieniowania** w [Shader Designer](../designers/shader-designer.md)  
  
 Poniższa ilustracja przedstawia programu do cieniowania, który jest opisany w tym dokumencie dotyczą w scenie 3-D, która została przedstawiona w [jak: Modelowanie terenu 3D](../designers/how-to-model-3-d-terrain.md). Intensywność koloru zwiększa się o wysokości punktów na całym świecie.  
  
 ![Efekt gradientu stosowane do 3&#45;modelu terenu D](../designers/media/digit-gradient-effect-result.png "cyfry-gradientu — efekt — wynik")  
  
 Aby uzyskać więcej informacji dotyczących sposobu stosowania programu do cieniowania do modelu 3-D, zobacz [jak: Stosowanie cieniowania do modelu 3-D](../designers/how-to-apply-a-shader-to-a-3-d-model.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Instrukcje: Stosowanie cieniowania do modelu 3-D](../designers/how-to-apply-a-shader-to-a-3-d-model.md)   
 [Instrukcje: Eksport cieniowania](../designers/how-to-export-a-shader.md)   
 [Instrukcje: Model terenu 3D](../designers/how-to-model-3-d-terrain.md)   
 [Instrukcje: Tworzenie cieniowania tekstury skali szarości](../designers/how-to-create-a-grayscale-texture-shader.md)   
 [Projektant programu do cieniowania](../designers/shader-designer.md)   
 [Węzły projektanta cieniowania](../designers/shader-designer-nodes.md)
