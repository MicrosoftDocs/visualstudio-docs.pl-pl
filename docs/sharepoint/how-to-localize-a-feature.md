---
title: 'Instrukcje: Lokalizowanie funkcji | Dokumentacja firmy Microsoft'
ms.date: 02/02/2017
ms.topic: conceptual
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
ms.openlocfilehash: f6e796cc00478ee823c345fd02738f8677c36373
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60074641"
---
# <a name="how-to-localize-a-feature"></a>Instrukcje: Lokalizowanie funkcji
  Domyślnie funkcja tytuły i opisy używa ciągu ustalonych wartości. Aby zlokalizować funkcję tytuł i opis, Zastąp ciągi wyrażeń, które odwołują się zlokalizowanych zasobów.

## <a name="localize-a-feature"></a>Lokalizowanie funkcji

#### <a name="to-localize-a-feature"></a>Aby zlokalizować funkcję

1. W **Eksploratora rozwiązań**, otwórz menu skrótów dla **Feature1** węzła, a następnie wybierz **Dodaj zasób funkcji**.

2. W **Dodaj zasób** okna dialogowego wybierz **Język niezmienny** na liście kultury dla języka domyślnego pliku zasobów funkcji.

3. Powtórz poprzedni krok dla każdego lokalizowanego języka, wybierając języki wybranej funkcji zlokalizowane pliki zasobów.

     Pliki zasobów oddzielne funkcji są tworzone: jeden dla języka domyślnego i jeden dla każdego zlokalizowanego języka, które mają być obsługiwane.

4. Otwórz każdy plik zasobów w edytorze zasobów, a następnie wprowadź wszystkie identyfikatory parametrów i ich wartości.

     Na przykład w domyślnym pliku zasobów funkcji, wprowadź identyfikator ciągu **tytuł** o wartości **Mój tytuł funkcji**, a drugi ciąg Identyfikatora **opis** o wartości **Mój opis funkcji**. Dla każdego zlokalizowanego pliku zasobów Użyj tego samego ciągu identyfikatorów używane w domyślnej zasobu funkcji, ale wprowadź zlokalizowanych ciągów dla wartości.

5. Po wprowadzeniu wszystkich wartości zasobów, otwórz menu skrótów dla funkcji (na przykład *Feature1.feature*), a następnie wybierz **Projektant widoków** aby otworzyć tę funkcję w Projektancie funkcji.

6. Aby zlokalizować **tytuł** i **opis** pól w funkcji, użyj następującego formatu wprowadź wartości w polach ich:

     `$Resources:` *Identyfikator ciągu*

     Na przykład, wprowadź $Resources:**tytuł** w **tytuł funkcji** pole i $Resources:**opis** w **opis funkcji** okno .

     Ciąg identyfikatory muszą być zgodne te, które są używane w plikach zasobów.

7. Wybierz **F5** klawisz, aby skompilować i uruchomić aplikację.

8. W programie SharePoint, należy otworzyć **Akcje witryny** menu, wybierz **ustawienia lokacji**, a następnie w **Akcje witryny** wybierz sekcję **Zarządzanie funkcji witryny** łącza.

9. W programie SharePoint zmień język wyświetlania z domyślnego.

     Funkcja zlokalizowane tytuły i opisy są wyświetlane w aplikacji. Aby wyświetlić zasoby zlokalizowane, serwer programu SharePoint musi mieć zainstalowany pakiet językowy pasujący plik zasobów kultury.

## <a name="see-also"></a>Zobacz także
- [Lokalizowanie rozwiązań SharePoint](../sharepoint/localizing-sharepoint-solutions.md)
- [Instrukcje: Dodawanie pliku zasobu](../sharepoint/how-to-add-a-resource-file.md)
- [Instrukcje: Lokalizowanie znacznika ASPX](../sharepoint/how-to-localize-aspx-markup.md)
- [Instrukcje: Lokalizowanie kodu](../sharepoint/how-to-localize-code.md)
