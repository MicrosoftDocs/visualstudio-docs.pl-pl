---
title: 'Instrukcje: Localize ASPX Markup | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: conceptual
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
ms.openlocfilehash: 433111855aab18bea412e5774cfe7a2fca2b2a7b
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56609829"
---
# <a name="how-to-localize-aspx-markup"></a>Instrukcje: Lokalizowanie znacznika ASPX
  [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] (aspx) stron zazwyczaj używają ciągu ustalonych wartości. Aby zlokalizować te ciągi, należy zastąpić je za pomocą wyrażeń, które odwołują się zlokalizowanych zasobów.

## <a name="localize-aspx-markup"></a>Lokalizowanie znacznika ASPX

#### <a name="to-localize-aspx-markup"></a>Do zlokalizowania znaczników ASPX

1.  Dodaj pliki zasobów oddzielne: jeden dla języka domyślnego i jeden dla każdego zlokalizowanego języka.

     Jeśli lokalizujesz wyłącznie znaczników i kodu nie można dodać elementu projektu globalnego pliku zasobów. Jeśli lokalizujesz kodu i znaczników, Dodaj element projektu pliku zasobów.

    1.  Aby dodać plik zasobów globalnych w **Eksploratora rozwiązań**, otwórz menu skrótów dla elementu projektu programu SharePoint, a następnie wybierz **Dodaj** > **nowy element**. W ramach programu SharePoint **2010** węzła, wybierz **plik zasobów globalnych** szablonu.

    2.  Aby dodać plik zasobów w **Eksploratora rozwiązań**, otwórz menu skrótów dla elementu projektu programu SharePoint, a następnie wybierz **Dodaj** > **nowy element**. W obszarze **języka Visual Basic** lub **Visual C#**  węzła, wybierz **plik zasobów** szablonu.

    > [!NOTE]
    >  Pamiętaj dodać pliki zasobów do elementu projektu programu SharePoint, aby włączyć właściwość typu wdrożenia. Ta właściwość jest wymagana w dalszej części tej procedury. Jeśli rozwiązanie nie ma elementu projektu programu SharePoint, możesz dodać pusty projekt programu SharePoint i Usuń domyślny *Elements.xml* pliku.

2.  Nadaj plikowi zasobów języka domyślnego nazwę wybraną z dołączonym *resx* rozszerzenie, np. MyAppResources.resx. Użyj tej samej nazwie bazowej dla każdego zlokalizowanego pliku zasobów, ale Dodaj kulturę [!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)]. Na przykład, nazwij niemieckie zlokalizowane zasoby *MyAppResources.de-DE.resx*.

3.  Zmień wartość właściwości **typu wdrożenia** właściwości każdego pliku zasobu na **AppGlobalResource** aby spowodować ich wdrażanie do folderu App_GlobalResources na serwerze.

4.  Jeśli używasz zasobów do lokalizowania kodu Oprócz oznakowania aspx, pozostaw wartość **Build Action** właściwości każdego plików jako **zasób osadzony**. Jeśli używasz plików zasobów tylko do zlokalizowania znaczników, opcjonalnie można zmienić wartość właściwości plików do **zawartości**. Aby uzyskać więcej informacji, zobacz [rozwiązań SharePoint lokalizowanie](../sharepoint/localizing-sharepoint-solutions.md).

5.  Otwórz każdy plik zasobów i Dodaj zlokalizowane ciągi, przy użyciu tego samego ciągu identyfikatorów w każdym pliku.

6.  W [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] znaczników strony ASPX lub formantu, Zastąp zakodowane sprzętowo ciągi wartościami, które należy użyć następującego formatu:

    ```aspx-csharp
    <%$Resources:Resource File Name, String ID%>
    ```

     Na przykład aby zlokalizować tekstu dla formantu etykiety na stronę aplikacji, możesz zmienić:

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

7.  Wybierz **F5** klawisz, aby skompilować i uruchomić aplikację.

8.  W programie SharePoint zmień język wyświetlania z domyślnego.

     W aplikacji, pojawiają się zlokalizowane ciągi. Aby wyświetlić zasoby zlokalizowane, serwer programu SharePoint musi mieć zainstalowany pakiet językowy pasujący plik zasobów kultury.

## <a name="see-also"></a>Zobacz także
- [Lokalizowanie rozwiązań SharePoint](../sharepoint/localizing-sharepoint-solutions.md)
- [Instrukcje: Lokalizowanie funkcji](../sharepoint/how-to-localize-a-feature.md)
- [Instrukcje: Dodawanie pliku zasobu](../sharepoint/how-to-add-a-resource-file.md)
- [Instrukcje: Lokalizowanie kodu](../sharepoint/how-to-localize-code.md)
