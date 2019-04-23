---
title: Tworzenie nowego testu usługi internetowej
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- Web performance tests, creating Web service tests
- Web services [Visual Studio ALM], creating
- service tests, Web
ms.assetid: fbcd57ee-06ad-4260-8694-09f8e0f93e39
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 3fd640a79a81e2306c8abd1c3c5279b1fc8f335f
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60065366"
---
# <a name="how-to-create-a-web-service-test"></a>Instrukcje: Tworzenie testu usługi internetowej

Test wydajności sieci web służy do testowania usług sieci web. Za pomocą **Wstaw żądanie** i **Wstaw żądanie usługi sieci Web** opcje, można dostosować poszczególne żądania w **edytora testów wydajności sieci Web** można zlokalizować w sieci web strony usługi. Zazwyczaj tych stron nie wyświetla w aplikacji sieci web. W związku z tym należy dostosować żądanie, aby uzyskać do nich dostęp.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

W poniższych procedurach użyto usługi sieci web, która jest zawarta w Commerce Starter Kit. Możesz ją pobrać z [ASP.NET commerce starter kit](http://go.microsoft.com/fwlink/?LinkId=181469).

**Wymagania**

Visual Studio Enterprise

## <a name="to-test-a-web-service"></a>Aby przetestować usługę sieci web

1. Utwórz nowy test wydajności sieci web. Zaraz po otwarciu przeglądarki, wybierz **zatrzymać**.

2. W **edytora testów wydajności sieci Web**, kliknij prawym przyciskiem myszy test wydajności sieci web i wybierz **Dodaj żądanie usługi sieci Web**.

3. W **adresu Url** właściwości nowego żądania wpisz nazwę usługi sieci web, takich jak **http://localhost/storecsvs/InstantOrder.asmx**.

4. Otwórz oddzielną sesję przeglądarki i wpisz adres URL *.asmx* strony w **adres** paska narzędzi. Wybierz metodę, którą chcesz przetestować i uważnie przeczytaj komunikat protokołu SOAP. Zawiera on element `SOAPAction`.

5. W **edytora testów wydajności sieci Web**, kliknij prawym przyciskiem myszy żądanie i wybierz **Dodawanie nagłówka** Aby dodać nowy nagłówek. W **nazwa** właściwość, typ `SOAPAction`. W **wartość** właściwości, wpisz wartość, która zostanie wyświetlony w `SOAPAction`, takich jak `"http://tempuri.org/CheckStatus"`.

6. Rozwiń węzeł adresu URL w edytorze, wybierz polecenie **ciąg tekstowy** węzła i **typu zawartości** właściwości wprowadź wartość `text/xml`.

7. Wróć do przeglądarki z kroku 4 zaznacz fragment XML żądania SOAP ze strony opisu usługi sieci web i skopiuj go do Schowka.

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

9. Wróć do **edytora testów wydajności sieci Web** , a następnie wybierz przycisk wielokropka **(...)**  w **ciąg tekstowy** właściwości. Wklej zawartość schowka do właściwości.

10. Aby test kończył się pomyślnie, zamień wszystkie wartości wieloznaczne w kodzie XML prawidłowymi wartościami. W poprzednim przykładzie należy zamienić dwa wystąpienia wartości `string` i jedno wartości `int`. Ta operacja usługi sieci web zostanie wykonana tylko pod warunkiem istnieje zarejestrowany użytkownik, który złożył zamówienie.

11. Kliknij prawym przyciskiem myszy żądanie usługi sieci web, a następnie wybierz pozycję **Dodaj parametr QueryString adresu URL**.

12. Przypisz parametrowi ciągu zapytania nazwę i wartość. W poprzednim przykładzie nazwą jest `op` , a wartość to `CheckStatus`. Identyfikuje operację usługi sieci web do wykonania.

    > [!NOTE]
    > Powiązanie danych można używać w treści protokołu SOAP, można zmienić wszelkie wartości zastępcze wartościami powiązanymi z danymi za pomocą `{{DataSourceName.TableName.ColumnName}}` składni.

13. Uruchom test. W górnym okienku **podglądu wyników testu wydajności sieci Web**, zaznacz żądanie usługi sieci web. W dolnym okienku zaznacz kartę przeglądarki sieci web. Plik XML, który jest zwracany przez usługę sieci web oraz wyniki wszelkich operacji, zostaną wyświetlone.

## <a name="see-also"></a>Zobacz także

- [Tworzenie niestandardowych kodów i wtyczek dla testów obciążenia](../test/create-custom-code-and-plug-ins-for-load-tests.md)