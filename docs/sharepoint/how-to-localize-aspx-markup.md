---
title: 'Instrukcje: Lokalizowanie znacznika ASPX | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- localizing XML [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, localizing
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 63bd8ee614a78752069002820689a2cc6c0be783
ms.sourcegitcommit: f9e44f5ab6a1dfb56c945c9986730465e1adb6fc
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2020
ms.locfileid: "86016290"
---
# <a name="how-to-localize-aspx-markup"></a>Instrukcje: Lokalizowanie znacznika ASPX
  [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)]strony (. aspx) zazwyczaj używają zakodowanych wartości ciągu. Aby zlokalizować te ciągi, zastąp je wyrażeniami odwołującymi się do zlokalizowanych zasobów.

## <a name="localize-aspx-markup"></a>Lokalizowanie znacznika ASPX

#### <a name="to-localize-aspx-markup"></a>Aby zlokalizować znacznik ASPX

1. Dodaj oddzielne pliki zasobów: jeden dla języka domyślnego i jeden dla każdego zlokalizowanego języka.

     W przypadku lokalizowania tylko znaczników i nie kodu, Dodaj element projektu plik zasobów globalnych. W przypadku lokalizowania kodu i znaczników Dodaj element projektu plik zasobów.

    1. Aby dodać plik zasobów globalnych, w **Eksplorator rozwiązań**Otwórz menu skrótów dla elementu projektu programu SharePoint, a następnie wybierz polecenie **Dodaj**  >  **nowy element**. W węźle SharePoint **2010** wybierz szablon **pliku zasoby globalne** .

    2. Aby dodać plik zasobów, w **Eksplorator rozwiązań**Otwórz menu skrótów dla elementu projektu programu SharePoint, a następnie wybierz polecenie **Dodaj**  >  **nowy element**. W węźle **Visual Basic** lub **Visual C#** wybierz szablon **pliku Resources** .

    > [!NOTE]
    > Pamiętaj, aby dodać pliki zasobów do elementu projektu SharePoint, aby włączyć właściwość typ wdrożenia. Ta właściwość jest wymagana w dalszej części tej procedury. Jeśli Twoje rozwiązanie nie ma elementu projektu programu SharePoint, możesz dodać pusty projekt programu SharePoint i usunąć jego domyślny plik *Elements.xml* .

2. Nadaj plikowi zasobu języka domyślnego wybraną nazwę, która jest dołączana do rozszerzenia *resx* , np. MyAppResources. resx. Użyj tej samej nazwy bazowej dla każdego zlokalizowanego pliku zasobów, ale Dodaj kulturę [!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)] . Na przykład Nazwij plik niemiecki zlokalizowany zasób *MyAppResources.de-de. resx*.

3. Zmień wartość właściwości **typ wdrożenia** każdego pliku zasobu na **AppGlobalResource** , aby spowodować ich wdrożenie do folderu App_GlobalResources serwera.

4. Jeśli używasz zasobów do lokalizowania kodu oprócz znaczników ASPX, pozostaw wartość właściwości **Akcja kompilacji** każdego pliku jako **zasób osadzony**. Jeśli używasz plików zasobów tylko do lokalizowania znaczników, możesz opcjonalnie zmienić wartość właściwości plików na **zawartość**. Aby uzyskać więcej informacji, zobacz [Lokalizowanie rozwiązań SharePoint](../sharepoint/localizing-sharepoint-solutions.md).

5. Otwórz każdy plik zasobów i Dodaj zlokalizowane ciągi, używając tych samych identyfikatorów ciągów w każdym pliku.

6. W [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] znaczniku na stronie lub kontrolce aspx Zamień stałe ciągi z wartościami, które używają następującego formatu:

    ```aspx-csharp
    <%$Resources:Resource File Name, String ID%>
    ```

     Na przykład, aby zlokalizować tekst kontrolki etykieta na stronie aplikacji, należy zmienić:

    ```aspx-csharp
    <asp:Content ID="Main" ContentPlaceHolderID="PlaceHolderMain" runat="server">
    <asp:Label ID="lbl" runat="server" Text="Label text"></asp:Label>
    </asp:Content>
    ```

     na

    ```aspx-csharp
    <asp:Content ID="Main" ContentPlaceHolderID="PlaceHolderMain" runat="server">
    <asp:Label ID="lbl" runat="server" Text="<%$Resources:MyAppResources,String1%>"></asp:Label>
    </asp:Content>
    ```

7. Wybierz klawisz **F5** , aby skompilować i uruchomić aplikację.

8. W programie SharePoint Zmień język wyświetlania z domyślnego.

     Zlokalizowane ciągi pojawiają się w aplikacji. Aby wyświetlić zlokalizowane zasoby, na serwerze programu SharePoint musi być zainstalowany pakiet językowy zgodny z kulturą pliku zasobów.

## <a name="see-also"></a>Zobacz także
- [Lokalizowanie rozwiązań SharePoint](../sharepoint/localizing-sharepoint-solutions.md)
- [Instrukcje: Lokalizowanie funkcji](../sharepoint/how-to-localize-a-feature.md)
- [Instrukcje: Dodawanie pliku zasobów](../sharepoint/how-to-add-a-resource-file.md)
- [Instrukcje: lokalizowanie kodu](../sharepoint/how-to-localize-code.md)
