---
title: 'Instrukcje: Lokalizowanie kodu | Dokumentacja firmy Microsoft'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- localizing code [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, localizing
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 9f45ef99210ccf5e6caa22e4aef6ba303aa6a6b2
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53990795"
---
# <a name="how-to-localize-code"></a>Instrukcje: Lokalizowanie kodu
  Niezlokalizowany kod używa ciągu ustalonych wartości. Aby zlokalizowania ciągi kodów, zastąp je wywołaniami do <xref:System.Web.HttpContext.GetGlobalResourceObject%2A>, czyli metody, która odwołuje się do zlokalizowanych zasobów.  
  
## <a name="localize-code"></a>Lokalizowanie kodu  
  
#### <a name="to-localize-code"></a>Aby zlokalizować kod  
  
1.  W **Eksploratora rozwiązań**, otwórz menu skrótów dla elementu projektu, a następnie wybierz **Dodaj** > **modułu**.  
  
     Wybierz **plik zasobów** szablonu.  
  
    > [!NOTE]  
    >  Pamiętaj dodać plik zasobów do elementu projektu programu SharePoint, tak aby właściwość typu wdrażania była dostępna. Ta właściwość jest wymagana w dalszej części tej procedury.  
  
2.  Nadaj plikowi zasobów języka domyślnego nazwę wybraną z dołączonym *resx* rozszerzenia, takie jak *MyAppResources.resx*.  
  
3.  Powtórz kroki 1 i 2, aby dodać pliki zasobów oddzielne w elemencie projektu programu SharePoint: jeden dla każdego zlokalizowanego języka.  
  
     Użyj tej samej nazwie bazowej dla każdego zlokalizowanego pliku zasobów, ale Dodaj identyfikator kultury. Na przykład, nazwij niemieckie zlokalizowane zasoby *MyAppResources.de-DE.resx*.  
  
4.  Otwórz każdy plik zasobów i Dodaj zlokalizowane ciągi. Użyj tego samego ciągu identyfikatorów w każdym pliku.  
  
5.  Zmień wartość właściwości **typu wdrożenia** właściwości każdego pliku zasobu na **AppGlobalResource** na każdy plik wdrożyć do folderu App_GlobalResources na serwerze.  
  
6.  Pozostaw wartość **Build Action** właściwości każdego plików jako **zasób osadzony**.  
  
     Zasoby osadzone są kompilowane do projektu biblioteki DLL.  
  
7.  Skompiluj projekt, aby utworzyć satelitarne biblioteki DLL zasobu.  
  
8.  W **projektancie pakietu**, wybierz **zaawansowane** kartę, a następnie dodaj zestawu satelickiego.  
  
9. W **lokalizacji** pola, Dodaj folder ID kultury do ścieżki lokalizacji, takich jak *de-DE\\\<nazwy elementu projektu >. resources.dll*.  
  
10. Jeśli rozwiązanie nie odwołuje się jeszcze do zestawu System.Web, Dodaj odwołanie do niej i Dodaj dyrektywę w kodzie do <xref:System.Web>.  
  
11. Zlokalizuj wszystkie ciągi zakodowane sprzętowo, które są widoczne dla użytkowników, takie jak tekst interfejsu użytkownika, błędy i tekst komunikatu. Zastąp je wywołaniem do <xref:System.Web.HttpContext.GetGlobalResourceObject%2A> metody przy użyciu następującej składni:  
  
    ```csharp  
    HttpContext.GetGlobalResourceObject("Resource File Name", "String ID")  
    ```  
  
12. Wybierz **F5** klawisz, aby skompilować i uruchomić aplikację.  
  
13. W programie SharePoint zmień język wyświetlania z domyślnego.  
  
     W aplikacji, pojawiają się zlokalizowane ciągi. Aby wyświetlić zasoby zlokalizowane, serwer programu SharePoint musi mieć zainstalowany pakiet językowy pasujący plik zasobów kultury.  
  
## <a name="see-also"></a>Zobacz także
 [Lokalizowanie rozwiązań SharePoint](../sharepoint/localizing-sharepoint-solutions.md)   
 [Instrukcje: Lokalizowanie funkcji](../sharepoint/how-to-localize-a-feature.md)   
 [Instrukcje: Lokalizowanie znacznika ASPX](../sharepoint/how-to-localize-aspx-markup.md)   
 [Instrukcje: Dodawanie pliku zasobu](../sharepoint/how-to-add-a-resource-file.md)  
