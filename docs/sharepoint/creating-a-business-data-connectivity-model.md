---
title: Tworzenie modelu łączności danych firmowych | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Business Data Connectivity service [SharePoint development in Visual Studio], model
- BDC [SharePoint development in Visual Studio], creating a model
- Business Data Connectivity service [SharePoint development in Visual Studio], creating a model
- SharePoint development in Visual Studio, Business Data Connectivity service
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 9f3da13858507a3ff176aaa0a44051674fd5285f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "64788188"
---
# <a name="create-a-business-data-connectivity-model"></a>Tworzenie modelu łączności danych firmy
  Można utworzyć model łączności danych biznesowych (BDC) lub dostosować istniejący model usługi BDC przy użyciu programu Visual Studio. Każdy projekt programu SharePoint może zawierać tylko jeden model. Aby uzyskać więcej informacji, zobacz [Integrowanie danych firmowych z programem SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md).

## <a name="create-a-new-model"></a>Utwórz nowy model
 Aby utworzyć nowy model, należy utworzyć projekt **modelu usługi łączności danych firmy** lub dodać element **modelu łączności danych firmowych** do **pustego projektu programu SharePoint**.

> [!NOTE]
> [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)]Na komputerze musi być zainstalowany program.

 Program Visual Studio dodaje folder do projektu. Ten folder ma nazwę określoną dla elementu **model usługi łączności danych firmowych** w oknie dialogowym **Dodaj nowy element** . W przypadku tworzenia nowego projektu **modelu usługi łączności danych firmowych** program Visual Studio nazywa folder **BdcModel1**.

 Program Visual Studio dodaje do nowego folderu następujące pliki:

|Plik|Opis|
|----------|-----------------|
|Plik definicji modelu|Zawiera kod XML, który definiuje jednostki, metody, obiekty systemu LOB i inne metadane opisujące model.<br /><br /> Zmodyfikuj metadane w tym pliku przy użyciu okna Projektant BDC, **Eksplorator BDC**, okno **Szczegóły metody BDC** i okno **Właściwości** .|
|Plik kodu usługi jednostki|Zawiera metody służące do pobierania, aktualizowania i usuwania wystąpień jednostki domyślnej.|

 Aby zdefiniować właściwości jednostki, edytuj plik kodu podmiotu. Aby uzyskać więcej informacji, zobacz [jak: Dodawanie jednostki do modelu](../sharepoint/how-to-add-an-entity-to-a-model.md).

 Aby pobrać, zaktualizować i usunąć wystąpienia jednostki, Dodaj kod do pliku kodu usługi jednostki. Aby uzyskać więcej informacji, zobacz [Projektowanie modelu łączności danych firmowych](../sharepoint/designing-a-business-data-connectivity-model.md).

 Podczas kompilowania projektu, program Visual Studio tworzy zestaw. Upewnij się, że nie dodasz innych elementów do projektu, który dodaje kod do zestawu projektu (na przykład: **sekwencyjny element przepływu pracy** lub element **części sieci Web** ). Kod tego elementu nie zostanie uruchomiony podczas wdrażania rozwiązania, ponieważ pakiet rozwiązania nie kopiuje zestawu do globalnej pamięci podręcznej zestawów.  Pakiet rozwiązania wdraża zestaw w bazie danych usługi BDC tylko w programie SharePoint.

> [!NOTE]
> Program Visual Studio kopiuje zestaw do obu lokalizacji na komputerze lokalnym podczas debugowania projektu.

## <a name="add-an-existing-model"></a>Dodaj istniejący model
 Można zaimportować model, który został utworzony przy użyciu innych narzędzi, takich jak SharePoint Designer. Możesz zaimportować istniejący model do projektu w następujących sytuacjach:

- Aby dostosować model, który jest już wdrożony w farmie serwerów programu SharePoint.

- Aby spakować i wdrożyć istniejący model w wielu farmach serwerów programu SharePoint.

  W obu przypadkach nie ma to zmian w systemach LOB zdefiniowanych w modelu, który jest importowany i będzie nadal działał zgodnie z oczekiwaniami. Aby dodać istniejący model do projektu programu SharePoint, użyj okna dialogowego **Dodaj istniejący element** programu Visual Studio. Aby uzyskać więcej informacji, zobacz [jak: Dodawanie istniejącego pliku modelu usługi BDC do projektu programu SharePoint](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md).

  Możesz dodać System LOB typu .NET Framework zestawu do zaimportowanego modelu, wybierając opcję w **klasie LobSystem zestawu platformy .NET**. Dzięki temu można napisać niestandardowy kod i użyć projektanta do zdefiniowania metadanych dla zaimportowanego modelu.

## <a name="related-topics"></a>Powiązane tematy

|Tytuł|Opis|
|-----------|-----------------|
|[Instrukcje: Tworzenie modelu usługi BDC](../sharepoint/how-to-create-a-bdc-model.md)|Pokazuje, jak utworzyć nowy model usługi BDC.|
|[Instrukcje: Dodawanie istniejącego pliku modelu BDC do projektu programu SharePoint](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md)|Pokazuje, jak zaimportować istniejący model do projektu programu SharePoint.|
|[Instrukcje: korzystanie z pliku zasobu do określania zlokalizowanych nazw, właściwości i uprawnień](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)|Opisuje sposób dostarczania ciągów, które są scalane z metadanymi modelu, gdy model jest zużywany przez składnik Web Part lub stronę sieci Web.|
|[Instrukcje: uwzględnianie niestandardowego zestawu w funkcji BDC](../sharepoint/how-to-include-a-custom-assembly-in-a-bdc-feature.md)|Pokazuje, w jaki sposób dołączyć zestaw niestandardowy do funkcji.|
