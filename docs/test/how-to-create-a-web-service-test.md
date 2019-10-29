---
title: Utwórz test usługi sieci Web
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- Web performance tests, creating Web service tests
- Web services [Visual Studio ALM], creating
- service tests, Web
ms.assetid: fbcd57ee-06ad-4260-8694-09f8e0f93e39
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 90dae3add4782af18763168643cfa5755d37cc2e
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/28/2019
ms.locfileid: "72981275"
---
# <a name="how-to-create-a-web-service-test"></a>Instrukcje: Tworzenie testu usługi sieci Web

Aby przetestować usługi sieci Web, można użyć testu wydajności sieci Web. Za pomocą opcji **Wstaw żądanie** i **Wstaw żądanie usługi sieci Web** można dostosować poszczególne żądania w **Edytor internetowego testu wydajnościowego** , aby zlokalizować strony usługi sieci Web. Zwykle te strony nie są wyświetlane w aplikacji sieci Web. W związku z tym należy dostosować żądanie, aby uzyskać do nich dostęp.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

W poniższych procedurach jest używana usługa sieci Web, która jest zawarta w ramach zestawu Commerce Start Kit. Można go pobrać z [ASP.NET Commerce Start Kit](https://sourceforge.net/projects/ppcsk/).

**Requirements**

Visual Studio Enterprise

## <a name="to-test-a-web-service"></a>Aby przetestować usługę sieci Web

1. Utwórz nowy test wydajności sieci Web. Zaraz po otwarciu przeglądarki wybierz pozycję **Zatrzymaj**.

2. W **Edytor internetowego testu wydajnościowego**kliknij prawym przyciskiem myszy Test wydajności sieci Web i wybierz polecenie **Dodaj żądanie usługi sieci Web**.

3. W polu właściwości **adres URL** nowego żądania wpisz nazwę usługi sieci Web, np. **http://localhost/storecsvs/InstantOrder.asmx** .

4. Otwórz oddzielną sesję przeglądarki i wpisz adres URL strony *. asmx* na pasku narzędzi **adresu** . Wybierz metodę, którą chcesz przetestować i uważnie przeczytaj komunikat protokołu SOAP. Zawiera on element `SOAPAction`.

5. W **Edytor internetowego testu wydajnościowego**kliknij prawym przyciskiem myszy żądanie i wybierz pozycję **Dodaj nagłówek** , aby dodać nowy nagłówek. W właściwości **name** wpisz `SOAPAction`. We właściwości **Value** wpisz wartość wyświetlaną w `SOAPAction`, na przykład `"http://tempuri.org/CheckStatus"`.

6. Rozwiń węzeł adresu URL w edytorze, wybierz węzeł **treść ciągu** i we właściwości **Typ zawartości** wprowadź wartość `text/xml`.

7. Wróć do przeglądarki w kroku 4, wybierz część XML żądania SOAP ze strony Opis usługi sieci Web i skopiuj ją do Schowka.

8. Zawartość XML przypomina poniższy przykład:

     ```xml
     <?xml version="1.0" encoding="utf-8"?>
     <soap:Envelope xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/">
     <soap:Body>
       <CheckStatus xmlns="http://tempuri.org/">
         <userName>string</userName>
         <password>string</password>
         <orderID>int</orderID>
       </CheckStatus>
     </soap:Body>
     </soap:Envelope>
     ```

9. Wróć do **Edytor internetowego testu wydajnościowego** a następnie wybierz wielokropek **(...)** we właściwości **treść ciągu** . Wklej zawartość schowka do właściwości.

10. Aby test kończył się pomyślnie, zamień wszystkie wartości wieloznaczne w kodzie XML prawidłowymi wartościami. W poprzednim przykładzie należy zamienić dwa wystąpienia wartości `string` i jedno wartości `int`. Ta operacja usługi sieci Web zostanie wykonana tylko wtedy, gdy istnieje zarejestrowany użytkownik, który złożył zamówienie.

11. Kliknij prawym przyciskiem myszy żądanie usługi sieci Web i wybierz polecenie **Dodaj parametr QueryString adresu URL**.

12. Przypisz parametrowi ciągu zapytania nazwę i wartość. W poprzednim przykładzie nazwa jest `op`, a wartość jest `CheckStatus`. Identyfikuje to operację usługi sieci Web, która ma zostać wykonana.

    > [!NOTE]
    > Możesz użyć powiązania danych w treści protokołu SOAP do zamiany dowolnej wartości symbolu zastępczego z wartościami powiązanymi z danymi przy użyciu składni `{{DataSourceName.TableName.ColumnName}}`.

13. Uruchom test. W górnym okienku **podglądu wyniki testów wydajności sieci Web**wybierz żądanie usługi sieci Web. W dolnym okienku wybierz kartę przeglądarka sieci Web. Zostanie wyświetlony kod XML, który jest zwracany przez usługę sieci Web i wyniki operacji.

## <a name="see-also"></a>Zobacz także

- [Tworzenie niestandardowych kodów i wtyczek dla testów obciążenia](../test/create-custom-code-and-plug-ins-for-load-tests.md)