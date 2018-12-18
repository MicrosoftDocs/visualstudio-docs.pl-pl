---
title: 'Porady: Określanie deskryptora typu parametru | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- Business Data Connectivity service [SharePoint development in Visual Studio], type descriptor
- BDC [SharePoint development in Visual Studio], parameter types
- BDC [SharePoint development in Visual Studio], type descriptor
- Business Data Connectivity service [SharePoint development in Visual Studio], parameter types
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: ec2b0173838446c770f3323aacefebabc195c48b
ms.sourcegitcommit: 0a8ac5f2a685270d9ca79bb39d26fd90099bfa29
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/09/2018
ms.locfileid: "51294984"
---
# <a name="how-to-define-the-type-descriptor-of-a-parameter"></a>Porady: Określanie deskryptora typu parametru
  Deskryptor typu zawiera właściwości, które opisują typ danych parametru. Deskryptor typu może zdefiniować pole, jednostkę lub kolekcję jednostek. Aby uzyskać więcej informacji, zobacz [TypeDescriptor](/previous-versions/office/developer/sharepoint-2007/ms543392\(v\=office.12\)).  
  
### <a name="to-define-the-type-descriptor-of-a-parameter"></a>Aby zdefiniować deskryptor typu parametru  
  
1.  W **szczegóły metody BDC** oknie Wybierz deskryptor typu parametru.  
  
2.  Na pasku menu wybierz **widoku**, **okno właściwości**.  
  
3.  W **właściwości** okna, ustaw właściwości deskryptora typu.  
  
     W poniższych procedurach opisano sposób definiowania deskryptora typu jako pola, jednostki lub kolekcja.  
  
### <a name="to-define-a-field"></a>Aby zdefiniować pole  
  
1.  W **właściwości** oknie **nazwa** właściwości deskryptora typu na nazwę pola w typie, która reprezentuje jednostkę (na przykład: **FirstName**).  
  
2.  Na liście obok **TypeName** właściwości, wybierz odpowiedni typ danych (na przykład **Int32**).  
  
     Aby uzyskać informacje na temat innych parametrów opcjonalnych, zobacz [TypeDescriptor](/previous-versions/office/developer/sharepoint-2007/ms543392\(v\=office.12\)).  
  
### <a name="to-define-an-entity"></a>Aby zdefiniować jednostkę  
  
1.  W **właściwości** oknie **nazwa** właściwość na nazwę opisującą element (na przykład: **skontaktuj się z pomocą**).  
  
2.  Ustaw **TypeName** właściwość w pełni kwalifikowaną nazwę typu, która reprezentuje jednostkę. Ten typ może być klasą w projekcie, typ zdefiniowany w zestawie, do którego można odwołać się w rozwiązaniu lub typem zdefiniowanym w modelu usługi BDC.  
  
    -   Klasy w projekcie, wybierz strzałkę w dół **TypeName** właściwości, wybierz **bieżący projekt** karty w oknie dialogowym zostanie wyświetlony, a następnie wybierz klasę w projekcie.  
  
         W pełni kwalifikowana nazwa obejmuje przestrzeń nazw i nazwę klasy, następuje nazwa systemu LOB. W poniższym przykładzie ustawiono wartość **TypeName** właściwości do klasy w projekcie.  
  
         `MyBDCNamespace.BdcModel1.Contact, BdcModel1`  
  
    -   Dla typu znajdującego się w zestawie w rozwiązaniu w pełni kwalifikowana nazwa obejmuje nazwę typu, nazwę zestawu, numer wersji, kulturę i token klucza publicznego.  
  
         W poniższym przykładzie ustawiono wartość **TypeName** właściwości Typ zdefiniowany w zestawie, do którego można odwołać się w rozwiązaniu.  
  
         `MyNamespace.Contact, myAssemblyName, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089`  
  
    -   Dla typu zdefiniowanego w modelu usługi BDC w pełni kwalifikowana nazwa obejmuje przestrzeń nazw i nazwę typu.  
  
         W poniższym przykładzie ustawiono wartość **TypeName** właściwość do typu w modelu usługi BDC.  
  
         `Microsoft.BusinessData.Runtime.DynamicType`  
  
3.  W **szczegóły metody BDC** , Otwórz listę, która pojawia się dla deskryptora typu, a następnie wybierz **Edytuj**.  
  
     **Eksplorator BDC** zostanie otwarte okno.  
  
4.  W **Eksplorator BDC**, otwórz menu skrótów deskryptora typu, a następnie wybierz **Dodaj deskryptor typu**.  
  
     Nowy deskryptor typu jest dodawany jako element podrzędny do deskryptora typu. Skonfiguruj ten deskryptor typu jako pole.  
  
5.  Powtórz krok 4, aby dodać deskryptor typu podrzędnego dla każdego pola encji.  
  
### <a name="to-define-a-collection-of-entities"></a>Aby zdefiniować kolekcję jednostek  
  
1. W **szczegóły metody BDC** oknie Wybierz deskryptor typu parametru, który chcesz.  
  
2. Na pasku menu wybierz **widoku**, **okno właściwości**.  
  
3. W **właściwości** oknie **nazwa** właściwość na nazwę opisującą element (na przykład: **kontakty**).  
  
4. Ustaw **IsCollection** właściwości **True**. Oznacza to, że ten deskryptor typu jest kolekcję jednostek.  
  
5. Ustaw **TypeName** właściwości na ciąg, który zawiera odwołanie do <xref:System.Collections.Generic.IEnumerable%601> interfejsu i w pełni kwalifikowaną nazwę typu, która reprezentuje jednostkę. Ten typ może być klasą w projekcie, typ zdefiniowany w zestawie, do którego można odwołać się w rozwiązaniu lub typem zdefiniowanym w modelu usługi BDC.  
  
   - Klasy w projekcie, wybierz strzałkę w dół **TypeName** właściwości, wybierz **bieżący projekt** karty w oknie dialogowym zostanie wyświetlony, a następnie wybierz klasę w projekcie.  
  
      W pełni kwalifikowana nazwa obejmuje przestrzeń nazw i nazwę klasy, następuje nazwa systemu LOB.  
  
      W poniższym przykładzie ustawiono wartość **TypeName** właściwości do kolekcji klas w projekcie.  
  
      `System.Collections.Generic.IEnumerable`1 [MyBDCNamespace.` ` BdcModel1.Contact, BdcModel1] "  
  
   - Dla typu znajdującego się w zestawie w rozwiązaniu w pełni kwalifikowana nazwa obejmuje nazwę typu, nazwę zestawu, numer wersji, kulturę i token klucza publicznego.  
  
      W poniższym przykładzie ustawiono wartość **TypeName** właściwości kolekcji typów w zestawie, do którego można odwołać się w rozwiązaniu.  
  
      `System.Collections.Generic.IEnumerable`1 [MyNamespace.Contact, myAssemblyName, wersja = 4.0.0.0, Culture = neutral, PublicKeyToken = b77a5c561934e089] "  
  
   - Dla typu zdefiniowanego w modelu usługi BDC w pełni kwalifikowana nazwa obejmuje tylko przestrzeń nazw i nazwę typu.  
  
      W poniższym przykładzie ustawiono wartość **TypeName** właściwości w kolekcji typów zdefiniowanych w modelu usługi BDC.  
  
      `System.Collections.Generic.IEnumerable`1 [Microsoft.BusinessData.Runtime.DynamicType] "  
  
6. W **szczegóły metody BDC** , Otwórz listę, która pojawia się dla deskryptora typu, a następnie wybierz **Edytuj**.  
  
    **Eksplorator BDC** zostanie otwarte okno.  
  
7. W **Eksplorator BDC**, otwórz menu skrótów deskryptora typu, a następnie wybierz **Dodaj deskryptor typu**.  
  
    Nowy deskryptor typu jest dodawany jako element podrzędny do deskryptora typu kolekcji. Skonfiguruj ten deskryptor typu jako jednostkę.  
  
## <a name="see-also"></a>Zobacz także
 [Omówienie narzędzi projektowania modelu BDC](../sharepoint/bdc-model-design-tools-overview.md)   
 [Porady: Dodawanie jednostki do modelu](../sharepoint/how-to-add-an-entity-to-a-model.md)   
 [Porady: Dodawanie parametru do metody](../sharepoint/how-to-add-a-parameter-to-a-method.md)   
 [Porady: Definiowanie wystąpienia metody](../sharepoint/how-to-define-a-method-instance.md)   
 [Projektowanie modelu łączności danych biznesowych](../sharepoint/designing-a-business-data-connectivity-model.md)  
  
