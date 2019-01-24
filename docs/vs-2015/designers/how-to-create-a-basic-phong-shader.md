---
title: 'Instrukcje: Tworzenie podstawowego modułu cieniowanie Phong | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: c7c69da8-142b-4d3b-9be9-4be0d5970b25
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: d5e4f1916fb7bfc0672efeddaac5e632692f92f9
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54787333"
---
# <a name="how-to-create-a-basic-phong-shader"></a>Instrukcje: Tworzenie podstawowego modułu cieniowanie Phong
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W tym dokumencie przedstawiono sposób umożliwia tworzenie oświetlenia modułu cieniującego, który implementuje Klasyczny model oświetlenie Phong Shader Designer i język programu do cieniowania wykres kierowany (DGSL).  
  
 Ten dokument przedstawia te działania:  
  
-   Dodawanie węzłów do wykresu programu do cieniowania  
  
-   Trwa rozłączanie węzłów  
  
-   Łączenie z węzłami  
  
## <a name="the-phong-lighting-model"></a>Model oświetlenie Phong  
 Model oświetlenie Phong rozszerza modelu oświetlenia Lamberta obejmujący odblasków wyróżnianie, która symuluje właściwości odbijające powierzchni. Odblasków składnik udostępnia dodatkowe oświetlenia z tego samego kierunkowe źródła światła, które są używane w modelu oświetlenia Lamberta, ale jej udziału ostateczny kolor jest przetwarzany inaczej. Wyróżnianie odblasków ma wpływ na co narażonego na ataki w scenie inaczej, na podstawie relacji między kierunku widoku, kierunek światła źródeł i orientację powierzchni. Jest to produkt koloru odblasków, moc odblasku i orientację powierzchni, a kolor, intensywność i kierunek źródła światła. Powierzchnie, które odzwierciedlają źródło światła bezpośrednio w przeglądarce otrzymują maksymalny udział odblasków i powierzchnie, które odzwierciedlają po stronie źródła światła od obserwatora otrzymywać nie materiałów przekazywanych. W obszarze model Phong oświetlenia co najmniej jednego składnika odblasków są łączone w celu określenia koloru i intensywność światła odblasków wyróżnianie dla każdego punktu w obiekcie i następnie są dodawane do wyniku modelu oświetlenia Lamberta, aby wygenerować ostateczny koloru piksela .  
  
 Aby uzyskać więcej informacji na temat modelu oświetlenia Lamberta zobacz [jak: Tworzenie podstawowego modułu cieniującego Lamberta](../designers/how-to-create-a-basic-lambert-shader.md).  
  
 Przed rozpoczęciem upewnij się, że **właściwości** okna i **przybornika** są wyświetlane.  
  
#### <a name="to-create-a-phong-shader"></a>Aby utworzyć cieniowanie Phong  
  
1. Tworzenie modułu cieniującego Lamberta zgodnie z opisem w [jak: Tworzenie podstawowego modułu cieniującego Lamberta](../designers/how-to-create-a-basic-lambert-shader.md).  
  
2. Odłącz **Lamberta** węzła z **ostateczny kolor** węzła. Wybierz **RGB** terminali z **Lamberta** węzła, a następnie wybierz **Przerwij linki**. To sprawia, że miejsce na węzeł, który zostanie dodany do następnego kroku.  
  
3. Dodaj **Dodaj** węzła do wykresu. W **przybornika**w obszarze **matematyczne**, wybierz opcję **Dodaj** i przenieś go do powierzchni projektowej.  
  
4. Dodaj **Specular** węzła do wykresu. W **przybornika**w obszarze **narzędzie**, wybierz opcję **Specular** i przenieś go do powierzchni projektowej.  
  
5. Dodaj udział odblasków. Przenieś **dane wyjściowe** terminali z **Specular** węzeł, aby **X** terminali z **Dodaj** węzeł, a następnie przenieść **danych wyjściowych**  terminali z **Lamberta** węzeł **Y** terminali z **Dodaj** węzła. Te połączenia łączyć wkładów całkowita kolor rozpraszania i odblasków dla piksela.  
  
6. Połącz się ostateczny kolor z wartości obliczanej koloru. Przenieś **dane wyjściowe** terminali z **Dodaj** węzeł **RGB** terminali z **ostateczny kolor** węzła.  
  
   Poniższej ilustracji ukończone programu do cieniowania programu graph i wersję zapoznawczą programu do cieniowania, zastosowano do modelu czajniczek.  
  
> [!NOTE]
>  Aby lepiej zaprezentować efekt programu cieniującego na tej ilustracji, została określona za pomocą koloru pomarańczowego **MaterialDiffuse** parametr programu do cieniowania i wyszukiwanie metal zakończenia została określona za pomocą **MaterialSpecular** i **MaterialSpecularPower** parametrów. Informacje o parametrach materiału sekcja Podgląd cieniowania w [Shader Designer](../designers/shader-designer.md).  
  
 ![Wykres modułu cieniującego i podgląd efektów jej](../designers/media/digit-lighting-graph.png "cyfry-oświetlenia-Graph")  
  
 Niektórych kształtów udostępniać lepsze wersje zapoznawcze niektórych programów do cieniowania. Aby uzyskać więcej informacji na temat programów do cieniowania w projektancie programu do cieniowania w wersji zapoznawczej, zobacz sekcję Podgląd cieniowania w [Shader Designer](../designers/shader-designer.md)  
  
 Poniższa ilustracja przedstawia programu do cieniowania, który jest opisany w tym dokumencie zastosowano do modelu 3-D. **MaterialSpecular** właściwość jest ustawiona na (1,00 0,50, 0.20 lub nowszej, 0,00), a jego **MaterialSpecularPower** właściwość jest ustawiona na 16.  
  
> [!NOTE]
>  **MaterialSpecular** właściwość określa jawnego zakończenia materiału powierzchni. Powierzchni połysku wysokiej, takich jak szkło lub plastiku zwykle odblasków kolor, który jest jasny cień bieli. Powierzchnia metalowych zwykle mają kolor odblasku, który znajduje się w pobliżu jej kolor rozpraszania. Powierzchnia satynowa Zakończ zwykle mają kolor odblasku ciemny odcień szarości.  
>   
>  **MaterialSpecularPower** właściwość określa, jak intensywne są światłem odbitym. Wysoka uprawnień odblasków symulować bardziej matowe, zlokalizowany więcej wyróżnia. Bardzo niskie uprawnień odblasków symulować intensywne, polegających na usuwaniu najważniejsze funkcje, które oversaturate i Ukryj kolor całej powierzchni.  
  
 ![Oświetlenie Phong zastosowano do modelu](../designers/media/digit-lighting-model.png "cyfrę oświetlenia modelu")  
  
 Aby uzyskać więcej informacji dotyczących sposobu stosowania programu do cieniowania do modelu 3-D, zobacz [jak: Stosowanie cieniowania do modelu 3-D](../designers/how-to-apply-a-shader-to-a-3-d-model.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Instrukcje: Stosowanie cieniowania do modelu 3-D](../designers/how-to-apply-a-shader-to-a-3-d-model.md)   
 [Instrukcje: Eksport cieniowania](../designers/how-to-export-a-shader.md)   
 [Instrukcje: Tworzenie podstawowego modułu cieniującego Lamberta](../designers/how-to-create-a-basic-lambert-shader.md)   
 [Projektant programu do cieniowania](../designers/shader-designer.md)   
 [Węzły projektanta cieniowania](../designers/shader-designer-nodes.md)
