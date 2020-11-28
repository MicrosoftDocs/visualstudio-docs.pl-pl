---
title: 'Instrukcje: Lokalizowanie funkcji | Microsoft Docs'
description: Dowiedz się, jak lokalizować tytuły i opisy funkcji w programie SharePoint, zastępując twarde zakodowane wartości ciągu wyrażeniami odwołującymi się do zlokalizowanych zasobów.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- features [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, localizing
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 3865c11c67fd826e0ce914b6aeb88364da3212b7
ms.sourcegitcommit: 2244665d5a0e22d12dd976417f2a782e68684705
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/28/2020
ms.locfileid: "96305195"
---
# <a name="how-to-localize-a-feature"></a>Instrukcje: Lokalizowanie funkcji
  Domyślnie tytuły i opisy funkcji używają zakodowanych wartości ciągu. Aby zlokalizować tytuł i opis funkcji, Zastąp ciągi wyrażeniami odwołującymi się do zlokalizowanych zasobów.

## <a name="localize-a-feature"></a>Lokalizowanie funkcji

#### <a name="to-localize-a-feature"></a>Aby zlokalizować funkcję

1. W **Eksplorator rozwiązań** Otwórz menu skrótów dla węzła **Feature1** , a następnie wybierz pozycję **Dodaj zasób funkcji**.

2. W oknie dialogowym **Dodawanie zasobu** wybierz z listy **Język niezmienny** jako kulturę domyślnego pliku zasobów funkcji językowej.

3. Powtórz poprzedni krok dla każdego zlokalizowanego języka, wybierając wybrane języki dla zlokalizowanych plików zasobów funkcji.

     Tworzone są osobne pliki zasobów funkcji: jeden dla języka domyślnego i jeden dla każdego zlokalizowanego języka, który ma być obsługiwany.

4. Otwórz każdy plik zasobów w edytorze zasobów, a następnie wprowadź wszystkie identyfikatory ciągów i ich wartości.

     Na przykład w domyślnym pliku zasobów funkcji wprowadź identyfikator ciągu **tytułu** z wartością **mojego tytułu funkcji** oraz drugi identyfikator ciągu **opisu** z wartością **mojego opisu funkcji**. Dla każdego zlokalizowanego pliku zasobów Użyj tych samych identyfikatorów ciągów, które są używane w domyślnym zasobie funkcji, ale wprowadź zlokalizowane ciągi dla wartości.

5. Po wprowadzeniu wszystkich wartości zasobów Otwórz menu skrótów dla funkcji (na przykład *Feature1. feature*), a następnie wybierz polecenie **Projektant widoków** , aby otworzyć funkcję w Projektancie funkcji.

6. Aby zlokalizować pola **tytuł** i **Opis** w funkcji, użyj następującego formatu, aby wprowadzić wartości w polach:

     `$Resources:`*Identyfikator ciągu*

     Na przykład wprowadź $Resources:**title** w polu **tytuł funkcji** i $Resources:**Description** w polu **Opis funkcji** .

     Identyfikatory ciągów muszą być zgodne z nazwami, które są używane w plikach zasobów.

7. Wybierz klawisz **F5** , aby skompilować i uruchomić aplikację.

8. W programie SharePoint otwórz menu **Akcje witryny** , wybierz pozycję **Ustawienia witryny**, a następnie w sekcji **Akcje lokacji** wybierz łącze **Zarządzaj funkcjami lokacji** .

9. W programie SharePoint Zmień język wyświetlania z domyślnego.

     Zlokalizowany tytuł i opis funkcji są wyświetlane w aplikacji. Aby wyświetlić zlokalizowane zasoby, na serwerze programu SharePoint musi być zainstalowany pakiet językowy zgodny z kulturą pliku zasobów.

## <a name="see-also"></a>Zobacz też
- [Lokalizowanie rozwiązań SharePoint](../sharepoint/localizing-sharepoint-solutions.md)
- [Instrukcje: Dodawanie pliku zasobów](../sharepoint/how-to-add-a-resource-file.md)
- [Instrukcje: Lokalizowanie znacznika ASPX](../sharepoint/how-to-localize-aspx-markup.md)
- [Instrukcje: lokalizowanie kodu](../sharepoint/how-to-localize-code.md)
