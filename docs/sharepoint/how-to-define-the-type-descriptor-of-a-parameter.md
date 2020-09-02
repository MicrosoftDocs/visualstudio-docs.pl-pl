---
title: 'Instrukcje: Definiowanie deskryptora typu dla parametru | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Business Data Connectivity service [SharePoint development in Visual Studio], type descriptor
- BDC [SharePoint development in Visual Studio], parameter types
- BDC [SharePoint development in Visual Studio], type descriptor
- Business Data Connectivity service [SharePoint development in Visual Studio], parameter types
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 0b3ae803576c98a86a45d175af45aa28b3852134
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "86016845"
---
# <a name="how-to-define-the-type-descriptor-of-a-parameter"></a>Instrukcje: Definiowanie deskryptora typu dla parametru
  Deskryptor typu zawiera właściwości opisujące typ danych parametru. Deskryptor typu może definiować pole, jednostkę lub kolekcję jednostek. Aby uzyskać więcej informacji, zobacz [TypeDescriptor](/previous-versions/office/developer/sharepoint-2007/ms543392\(v\=office.12\)).

### <a name="to-define-the-type-descriptor-of-a-parameter"></a>Aby zdefiniować deskryptor typu dla parametru

1. W oknie **Szczegóły metody BDC** wybierz deskryptor typu parametru.

2. Na pasku menu wybierz **Widok**, **okno właściwości**.

3. W oknie **Właściwości** ustaw właściwości deskryptora typu.

     W poniższych procedurach opisano sposób definiowania deskryptora typu jako pola, jednostki lub kolekcji jednostek.

### <a name="to-define-a-field"></a>Aby zdefiniować pole

1. W oknie **Właściwości** ustaw właściwość **Nazwa** deskryptora typu na nazwę pola w typie, który reprezentuje jednostkę (na przykład: **FirstName**).

2. Na liście obok właściwości **TypeName** wybierz odpowiedni typ danych (na przykład **Int32**).

     Aby uzyskać informacje o innych opcjonalnych parametrach, zobacz [TypeDescriptor](/previous-versions/office/developer/sharepoint-2007/ms543392\(v\=office.12\)).

### <a name="to-define-an-entity"></a>Aby zdefiniować jednostkę

1. W oknie **Właściwości** ustaw właściwość **Nazwa** na nazwę opisującą jednostkę (na przykład: **Contact**).

2. Ustaw właściwość **TypeName** na w pełni kwalifikowaną nazwę typu, który reprezentuje jednostkę. Ten typ może być klasą w projekcie, typem zdefiniowanym w zestawie, do którego odwołuje się w rozwiązaniu lub typem zdefiniowanym w modelu obiektów BDC.

    - Dla klasy w projekcie, wybierz strzałkę w dół obok właściwości **TypeName** , wybierz kartę **bieżący projekt** w wyświetlonym oknie dialogowym, a następnie wybierz klasę w projekcie.

         W pełni kwalifikowana nazwa zawiera przestrzeń nazw i nazwę klasy, po której następuje nazwa systemu LOB. W poniższym przykładzie ustawiono wartość właściwości **TypeName** do klasy w projekcie.

         `MyBDCNamespace.BdcModel1.Contact, BdcModel1`

    - Dla typu znajdującego się w zestawie w rozwiązaniu, w pełni kwalifikowana nazwa zawiera nazwę typu, nazwę zestawu, numer wersji, kulturę i token klucza publicznego.

         W poniższym przykładzie ustawiono wartość właściwości **TypeName** do typu zdefiniowanego w zestawie, do którego odwołuje się w rozwiązaniu.

         `MyNamespace.Contact, myAssemblyName, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089`

    - W przypadku typu zdefiniowanego w modelu obiektów BDC w pełni kwalifikowana nazwa obejmuje przestrzeń nazw i nazwę typu.

         W poniższym przykładzie ustawiono wartość właściwości **TypeName** do typu w modelu obiektów BDC.

         `Microsoft.BusinessData.Runtime.DynamicType`

3. W oknie **Szczegóły metody BDC** Otwórz listę, która jest wyświetlana dla deskryptora typu, a następnie wybierz polecenie **Edytuj**.

     Zostanie otwarte okno **Eksplorator BDC** .

4. W **Eksploratorze BDC**Otwórz menu skrótów deskryptora typu, a następnie wybierz **Dodaj deskryptor typu**.

     Nowy deskryptor typu jest dodawany jako element podrzędny do deskryptora typu jednostki. Skonfiguruj ten deskryptor typu jako pole.

5. Powtórz krok 4, aby dodać deskryptor typu podrzędnego dla każdego pola jednostki.

### <a name="to-define-a-collection-of-entities"></a>Aby zdefiniować kolekcję jednostek

1. W oknie **Szczegóły metody BDC** wybierz deskryptor typu dla żądanego parametru.

2. Na pasku menu wybierz **Widok**, **okno właściwości**.

3. W oknie **Właściwości** ustaw właściwość **Nazwa** na nazwę opisującą jednostkę (na przykład: **kontakty**).

4. Ustaw właściwość **IsCollection** na **wartość true**. Oznacza to, że ten deskryptor typu jest kolekcją jednostek.

5. Ustaw właściwość **TypeName** na ciąg, który zawiera odwołanie do <xref:System.Collections.Generic.IEnumerable%601> interfejsu, oraz w pełni kwalifikowaną nazwę typu, który reprezentuje jednostkę. Ten typ może być klasą w projekcie, typem zdefiniowanym w zestawie, do którego odwołuje się w rozwiązaniu lub typem zdefiniowanym w modelu obiektów BDC.

   - Dla klasy w projekcie, wybierz strzałkę w dół obok właściwości **TypeName** , wybierz kartę **bieżący projekt** w wyświetlonym oknie dialogowym, a następnie wybierz klasę w projekcie.

      W pełni kwalifikowana nazwa zawiera przestrzeń nazw i nazwę klasy, po której następuje nazwa systemu LOB.

      W poniższym przykładzie ustawiono wartość właściwości **TypeName** do kolekcji klas w projekcie.

      `System.Collections.Generic.IEnumerable`1 [MyBDCNamespace. BdcModel1. Contact, BdcModel1] "

   - Dla typu znajdującego się w zestawie w rozwiązaniu, w pełni kwalifikowana nazwa zawiera nazwę typu, nazwę zestawu, numer wersji, kulturę i token klucza publicznego.

      W poniższym przykładzie ustawiono wartość właściwości **TypeName** do kolekcji typów w zestawie, do którego odwołuje się w rozwiązaniu.

      `System.Collections.Generic.IEnumerable`1 [przestrzeń nazw. Contact, nazwa zestawu, Version = 4.0.0.0, Culture = neutral, PublicKeyToken = b77a5c561934e089] "

   - W przypadku typu zdefiniowanego w modelu obiektów BDC w pełni kwalifikowana nazwa zawiera tylko przestrzeń nazw i nazwę typu.

      W poniższym przykładzie ustawiono wartość właściwości **TypeName** do kolekcji typów zdefiniowanych w modelu obiektów BDC.

      `System.Collections.Generic.IEnumerable`1 [Microsoft. BusinessData. Runtime. DynamicType] "

6. W oknie **Szczegóły metody BDC** Otwórz listę, która jest wyświetlana dla deskryptora typu, a następnie wybierz polecenie **Edytuj**.

    Zostanie otwarte okno **Eksplorator BDC** .

7. W **Eksploratorze BDC**Otwórz menu skrótów deskryptora typu, a następnie wybierz **Dodaj deskryptor typu**.

    Nowy deskryptor typu jest dodawany jako element podrzędny do deskryptora typu kolekcji. Skonfiguruj ten deskryptor typu jako jednostkę.

## <a name="see-also"></a>Zobacz też
- [Omówienie narzędzi projektowania modelu BDC](../sharepoint/bdc-model-design-tools-overview.md)
- [Instrukcje: Dodawanie jednostki do modelu](../sharepoint/how-to-add-an-entity-to-a-model.md)
- [Instrukcje: Dodawanie parametru do metody](../sharepoint/how-to-add-a-parameter-to-a-method.md)
- [Instrukcje: Definiowanie wystąpienia metody](../sharepoint/how-to-define-a-method-instance.md)
- [Projektowanie modelu łączności danych firmy](../sharepoint/designing-a-business-data-connectivity-model.md)
