---
title: Używanie modułów do dołączania plików w rozwiązaniu | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, deployment modules
- SharePoint development in Visual Studio, modules
- modules [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 4f8f2aa6c5d86af2424a811b6167829cefdb6fb5
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/28/2019
ms.locfileid: "72985297"
---
# <a name="use-modules-to-include-files-in-the-solution"></a>Używanie modułów do dołączania plików w rozwiązaniu
  Mogą wystąpić sytuacje, w których można chcieć wdrożyć pliki na serwerze programu SharePoint, niezależnie od ich typu plików, na przykład nowych stron wzorcowych. W tym celu można użyć *modułów* (nie należy mylić z [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] modułów kodu). Moduły są kontenerami dla plików w rozwiązaniu programu SharePoint. Po wdrożeniu rozwiązania pliki w module są kopiowane do określonych folderów na serwerze programu SharePoint.

## <a name="module-items-and-elements"></a>Elementy modułu i elementy
 Aby utworzyć moduł, Dodaj go do projektu, wybierając go w oknie dialogowym **Dodaj nowy element** . Następnie zmodyfikuj plik *. XML* , aby uwzględnić nazwy plików, które mają zostać wdrożone, gdzie znajdują się w systemie, i miejsce, w którym powinny być kopiowane na serwer programu SharePoint.

 Oto przykład pliku *Elements. XML* dla modułu:

```xml
<?xml version="1.0" encoding="utf-8"?>
<Elements xmlns="http://schemas.microsoft.com/sharepoint/">
    <Module Name="Module1">
        <File Path="Module1\Sample.txt" Url="Module1/Sample.txt" />
    </Module>
</Elements>

```

 Nowo utworzone moduły zawierają następujące pliki domyślne:

|Nazwa pliku|Opis|
|---------------|-----------------|
|*Elementy. XML*|Plik definicji modułu.|
|*Sample. txt*|Plik zastępczy, który służy jako przykład pliku w module.|

 Plik *Elements. XML* zawiera następujące elementy:

|Nazwa elementu|Opis|
|------------------|-----------------|
|Elementy|Zawiera wszystkie elementy zdefiniowane w module.|
|Moduł|Element module ma pojedynczy atrybut o *nazwie*, który określa nazwę modułu w formacie `<Module Name="Module1">`.<br /><br /> Należy pamiętać, że jeśli zmienisz nazwę modułu (lub jego właściwość *Nazwa folderu* ), musisz ręcznie zaktualizować nazwę w elemencie modułu.<br /><br /> Jeśli określisz podkatalog dla plików w module, [!INCLUDE[sharepointShort](../sharepoint/includes/sharepointshort-md.md)] (WSS) automatycznie utworzy zgodną strukturę katalogów.|
|Plik|Element pliku ma dwa parametry, *ścieżkę* i *adres URL*.<br /><br /> -Path: Nazwa i lokalizacja pliku w rozwiązaniu programu SharePoint. Format to, `Path="Module1\Sample.txt"`.<br /><br /> -URL: lokalizacja, w której plik zostanie wdrożony na serwerze programu SharePoint. Format to, `Url="Module1/Sample.txt"`.<br /><br /> -Type: opcjonalny atrybut, który ma dwa ustawienia: *GhostableInLibrary* i *Ghost*. Format to, `Type="GhostableInLibrary"`. Określenie *GhostableInLibrary* oznacza, że plik zostanie dodany do biblioteki dokumentów w programie SharePoint wraz z elementem listy, który będzie dołączany do pliku, gdy zostanie dodany do biblioteki. Określenie opcji z *duplikowaniem* powoduje, że plik zostanie dodany do programu SharePoint poza biblioteką dokumentów.|

 Każdy plik, który chcesz wdrożyć, wymaga oddzielnego wpisu elementu `<File>` w *elementach. XML*.

## <a name="see-also"></a>Zobacz także
- [Instrukcje: Dołączanie plików przy użyciu modułu](../sharepoint/how-to-include-files-by-using-a-module.md)
- [Instrukcje: Inicjowanie obsługi pliku](/previous-versions/office/developer/sharepoint-2010/ms441170(v=office.14))
- [Opracowywanie rozwiązań SharePoint](../sharepoint/developing-sharepoint-solutions.md)
- [Tworzenie składników Web Part dla programu SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)
- [Pakowanie i wdrażanie rozwiązań SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
