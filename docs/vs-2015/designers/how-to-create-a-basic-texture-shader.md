---
title: 'Instrukcje: Tworzenie cieniowania tekstury podstawowej | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: 5af113fb-6415-4be0-8b23-10fddb10e80a
caps.latest.revision: 25
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 59a926ab35e04aa120bc57250c3e5b2712858aa5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72664498"
---
# <a name="how-to-create-a-basic-texture-shader"></a>Porady: tworzenie cieniowania tekstury podstawowej
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W tym dokumencie przedstawiono sposób korzystania z projektanta programu do cieniowania i języka ukierunkowanego programu Graph (DGSL) w celu utworzenia cieniowania z jedną teksturą. Ten program do cieniowania ustawia końcowy kolor bezpośrednio na wartości RGB i alfa, które są próbkowane ze tekstury.

 W tym dokumencie przedstawiono następujące działania:

- Usuwanie węzłów z grafu programu do cieniowania

- Dodawanie węzłów do wykresu

- Ustawianie parametrów cieniowania

- Ustawianie widoczności parametrów

- Łączenie węzłów

## <a name="creating-a-basic-texture-shader"></a>Tworzenie cieniowania tekstury podstawowej
 Można zaimplementować podstawowe, jednoteksturowe cieniowanie, pisząc kolor i alfa próbki tekstury bezpośrednio do końcowego koloru wyjściowego.

 Przed rozpoczęciem upewnij się, że wyświetlane jest okno **Właściwości** i **Przybornik** .

#### <a name="to-create-a-basic-texture-shader"></a>Aby utworzyć cieniowanie tekstury podstawowej

1. Utwórz program do cieniowania DGSL. Aby dowiedzieć się, jak dodać cieniowanie DGSL do projektu, zobacz sekcję Wprowadzenie w [projektancie cieniowania](../designers/shader-designer.md).

2. Usuń węzeł **koloru punktu** . W obszarze tryb **wyboru** wybierz węzeł **Kolor punktu** , a następnie na pasku menu wybierz polecenie **Edytuj**, **Usuń**. Powoduje to powolne miejsce dla węzła, który jest dodawany w następnym kroku.

3. Dodaj **przykładowy węzeł tekstury** do grafu. W **przyborniku**, w obszarze **tekstura**wybierz pozycję **tekstura próbki** i przenieś ją na powierzchnię projektu.

4. Dodaj węzeł **współrzędnej tekstury** do grafu. W **przyborniku**, w obszarze **tekstura**wybierz pozycję **koordynuj współrzędne** i przenieś ją na powierzchnię projektu.

5. Wybierz teksturę, która ma zostać zastosowana. W obszarze tryb **wyboru** wybierz węzeł **przykład tekstury** , a następnie w oknie **Właściwości** Określ teksturę, która ma być używana przy użyciu właściwości **filename** .

6. Udostępnienie tekstury publicznie. Wybierz węzeł **przykład tekstury** , a następnie w oknie **Właściwości** ustaw właściwość **dostęp** na **publiczną**. Teraz można ustawić teksturę z innego narzędzia, takiego jak **Edytor modelu**.

7. Połącz Współrzędne tekstury z przykładem tekstury. W trybie **wyboru** Przenieś Terminal **wyjściowy** węzła **współrzędnej tekstury** do terminalu **UV** węzła **przykładu tekstury** . To połączenie służy do próbkowania tekstury na określonych współrzędnych.

8. Połącz próbkę tekstury z kolorem końcowym. Przenieś Terminal **RGB** z węzła **przykład tekstury** do terminalu **RGB** **końcowego węzła Color** , a następnie przenieś Terminal **alfa** węzła **przykładowego tekstury** do terminalu **alfa** **końcowego węzła koloru** .

   Na poniższej ilustracji przedstawiono ukończony wykres modułu cieniującego i Podgląd cieniowania zastosowany do modułu.

> [!NOTE]
> Na tej ilustracji, płaszczyzna jest używana jako kształt podglądu i określono teksturę, aby lepiej zademonstrować efekt cieniowania.

 ![Graf cieniowania i podgląd jego efektu](../designers/media/digit-texture-effect.png "Tekstura — efekt")

 Niektóre kształty mogą zapewniać lepszy Podgląd niektórych programów do cieniowania. Aby uzyskać więcej informacji na temat podglądu programów do cieniowania w projektancie cieniowania, zobacz [Projektant cieniowania](../designers/shader-designer.md) .

## <a name="see-also"></a>Zobacz też
 [Instrukcje: Stosowanie cieniowania do modelu trójwymiarowego](../designers/how-to-apply-a-shader-to-a-3-d-model.md) [edytora obrazów](../designers/image-editor.md) programu [cieniowania Designer](../designers/shader-designer.md) — [węzły projektanta cieniowania](../designers/shader-designer-nodes.md)
