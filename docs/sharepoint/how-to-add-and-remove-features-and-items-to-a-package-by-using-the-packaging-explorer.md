---
title: 'Eksplorator pakietów: Dodawanie & usuwanie funkcji & elementów do pakietu'
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
f1_keywords:
- VS.SharePointTools.RAD.PackagingExplorer
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, packages
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 9bc4546d598a2fcca822f1921f778034fb768c2b
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/30/2020
ms.locfileid: "91585592"
---
# <a name="how-to-add-and-remove-features-and-items-to-a-package-by-using-the-packaging-explorer"></a>Instrukcje: Dodawanie i usuwanie funkcji oraz elementów do pakietu przy użyciu Eksploratora pakietów
  Aby skonfigurować pakiet do wdrażania elementów i funkcji programu SharePoint, można użyć Eksploratora pakietów. Elementy projektu programu SharePoint i funkcje można dostosować wewnątrz pliku. wsp.

 Alternatywnie można użyć projektanta pakietów do wyświetlania i zmiany kolejności tych funkcji, aby zmienić kolejność aktywacji. Aby uzyskać więcej informacji, zobacz [jak: Dodawanie i usuwanie funkcji oraz elementów do pakietu przy użyciu projektanta pakietów](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-package-designer.md).

## <a name="open-the-packaging-explorer"></a>Otwórz Eksploratora pakietów
 Korzystając z poniższej procedury, można otworzyć Eksploratora pakietów, jeśli rozwiązanie Visual Studio zawiera co najmniej jeden projekt programu SharePoint. Alternatywnie Eksplorator pakietów otwiera się automatycznie podczas wyświetlania funkcji lub projektanta pakietów. Po zamknięciu wszystkich projektantów funkcji i pakietów Eksplorator pakietów zostanie również zamknięty.

#### <a name="to-open-the-packaging-explorer"></a>Aby otworzyć Eksploratora pakietów

1. Na pasku menu wybierz pozycję **Wyświetl**  >  **inne**  >  **Eksplorator pakietów**systemu Windows.

     **Eksplorator pakietów** zostanie wyświetlony w **przyborniku**.

## <a name="adding-a-feature-to-a-package"></a>Dodawanie funkcji do pakietu
 Nowe i istniejące funkcje można dodać do pakietu przy użyciu Eksploratora pakietów.

#### <a name="to-add-a-sharepoint-feature"></a>Aby dodać funkcję programu SharePoint

1. Otwórz **Eksploratora pakietów**, otwórz menu skrótów dla projektu, a następnie wybierz polecenie **Dodaj funkcję**.

#### <a name="to-move-an-existing-sharepoint-feature"></a>Aby przenieść istniejącą funkcję programu SharePoint

1. Otwórz **Eksploratora pakietów**, a następnie wykonaj jedną z następujących czynności:

    - Przeciągnij **funkcję** z jednego projektu do innego projektu.

    - Otwórz menu skrótów dla funkcji, wybierz polecenie **Wytnij**, otwórz menu skrótów dla projektu, do którego chcesz przenieść funkcję, a następnie wybierz **Wklej**.

    > [!NOTE]
    > Użyj tej procedury, jeśli masz więcej niż jeden projekt programu SharePoint w rozwiązaniu.

## <a name="validate-a-feature-or-package"></a>Weryfikowanie funkcji lub pakietu
 Możesz zidentyfikować potencjalne problemy w funkcjach i pakietach programu SharePoint, sprawdzając pliki. Ostrzeżenia i błędy są wyświetlane w oknie dane wyjściowe i w oknie Lista błędów.

#### <a name="to-validate-a-sharepoint-feature-or-package"></a>Aby sprawdzić poprawność funkcji lub pakietu programu SharePoint

1. Otwórz **Eksploratora pakietów**.

2. Otwórz menu skrótów dla funkcji lub pakietu, a następnie wybierz polecenie **Weryfikuj**.

## <a name="see-also"></a>Zobacz też
- [Pakowanie i wdrażanie rozwiązań SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
