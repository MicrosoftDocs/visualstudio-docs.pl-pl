---
title: Tworzenie testu usługi sieci Web
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- Web performance tests, creating Web service tests
- Web services [Visual Studio ALM], creating
- service tests, Web
ms.assetid: fbcd57ee-06ad-4260-8694-09f8e0f93e39
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 7a6e42d6d92a74a0fc8be96c966b9146b7888b9e
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75589100"
---
# <a name="how-to-create-a-web-service-test"></a>Instrukcje: Tworzenie nowego testu usługi internetowej

Można użyć testu wydajności sieci web do testowania usług sieci web. Korzystając z opcji **Wstaw żądanie i** **wstawianie żądania usługi sieci Web,** można dostosować poszczególne żądania w **Edytorze testów wydajności sieci Web,** aby zlokalizować strony usługi sieci web. Zazwyczaj nie są wyświetlane te strony w aplikacji sieci web. W związku z tym należy dostosować żądanie, aby uzyskać do nich dostęp.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Poniższe procedury używają usługi sieci web, która jest zawarta w Commerce Starter Kit. Możesz go pobrać z [ASP.NET commerce starter kit](https://sourceforge.net/projects/ppcsk/).

**Wymagania**

Visual Studio Enterprise

## <a name="to-test-a-web-service"></a>Aby przetestować usługę sieci web

1. Utwórz nowy test wydajności sieci Web. Gdy tylko przeglądarka się otworzy, wybierz pozycję **Zatrzymaj**.

2. W **Edytorze testów wydajności sieci Web**kliknij prawym przyciskiem myszy test wydajności sieci Web i wybierz polecenie Dodaj żądanie usługi sieci **Web**.

3. We właściwości **Url** nowego żądania wpisz nazwę usługi sieci web, taką jak **http://localhost/storecsvs/InstantOrder.asmx**.

4. Otwórz oddzielną sesję przeglądarki i wpisz adres URL strony *.asmx* na pasku narzędzi **Adres.** Wybierz metodę, którą chcesz przetestować i uważnie przeczytaj komunikat protokołu SOAP. Zawiera on element `SOAPAction`.

5. W **Edytorze testów wydajności sieci Web**kliknij prawym przyciskiem myszy żądanie i wybierz polecenie Dodaj **nagłówek,** aby dodać nowy nagłówek. We właściwości **Nazwa** `SOAPAction`wpisz . We właściwości **Wartość** wpisz wartość widoczna `SOAPAction`w `"http://tempuri.org/CheckStatus"`, na przykład .

6. Rozwiń węzeł adresu URL w edytorze, wybierz węzeł **Treść ciągu,** a we właściwości **Typ zawartości** wprowadź wartość `text/xml`.

7. Wróć do przeglądarki w kroku 4, wybierz część XML żądania PROTOKOŁU SOAP ze strony opisu usługi sieci web i skopiuj ją do schowka.

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

9. Wróć do **Edytora testów wydajności sieci Web,** a następnie wybierz wielokropek **(...)** we właściwości **Obiekt ciągu.** Wklej zawartość schowka do właściwości.

10. Aby test kończył się pomyślnie, zamień wszystkie wartości wieloznaczne w kodzie XML prawidłowymi wartościami. W poprzednim przykładzie należy zamienić dwa wystąpienia wartości `string` i jedno wartości `int`. Ta operacja usługi sieci web zostanie ukończona tylko wtedy, gdy zarejestrowany użytkownik złożył zamówienie.

11. Kliknij prawym przyciskiem myszy żądanie usługi sieci web i wybierz polecenie **Dodaj parametr querystring url**.

12. Przypisz parametrowi ciągu zapytania nazwę i wartość. W poprzednim przykładzie nazwa `op` jest i `CheckStatus`wartość jest . Identyfikuje operację usługi sieci web do wykonania.

    > [!NOTE]
    > Powiązanie danych w treści SOAP służy do zastępowania dowolnej wartości `{{DataSourceName.TableName.ColumnName}}` symbolu zastępczego wartościami powiązanymi z danymi przy użyciu składni.

13. Uruchom test. W górnym okienku **podglądu wyników testów wydajności sieci Web**wybierz żądanie usługi sieci web. W dolnym okienku wybierz kartę Przeglądarka internetowa. Zostanie wyświetlony kod XML zwracany przez usługę sieci web i wyniki wszelkich operacji.

## <a name="see-also"></a>Zobacz też

- [Tworzenie niestandardowych kodów i wtyczek dla testów obciążeniowych](../test/create-custom-code-and-plug-ins-for-load-tests.md)
