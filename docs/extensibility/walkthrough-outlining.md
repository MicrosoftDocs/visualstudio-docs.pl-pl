---
title: 'Przewodnik: Nakreślenie | Dokumenty firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - outlining
ms.assetid: d75a44aa-265a-44d4-9c28-457f59c4ff9f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 97b9dcbb2a24f1a3ed336a4a6bb7de4a15e907b4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697210"
---
# <a name="walkthrough-outlining"></a>Przewodnik: tworzenie konspektu
Skonfiguruj funkcje oparte na języku, takie jak konspekt, definiując rodzaje regionów tekstu, które chcesz rozwinąć lub zwinąć. Można zdefiniować regiony w kontekście usługi językowej lub zdefiniować własne rozszerzenie nazwy pliku i typ zawartości i zastosować definicję regionu tylko do tego typu lub zastosować definicje regionu do istniejącego typu zawartości (na przykład "tekst"). W tym przewodniku pokazano, jak zdefiniować i wyświetlić regiony przedstawiające.

## <a name="prerequisites"></a>Wymagania wstępne
 Począwszy od programu Visual Studio 2015, nie należy instalować visual studio SDK z centrum pobierania. Jest on dołączony jako opcjonalna funkcja w konfiguracji programu Visual Studio. Można również zainstalować vs SDK później. Aby uzyskać więcej informacji, zobacz [Instalowanie pakietu SDK programu Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-managed-extensibility-framework-mef-project"></a>Tworzenie projektu managed extensibility Framework (MEF)

### <a name="to-create-a-mef-project"></a>Aby utworzyć projekt MEF

1. Utwórz projekt VSIX. Nazwij `OutlineRegionTest`rozwiązanie .

2. Dodaj szablon elementu klasyfikatora edytora do projektu. Aby uzyskać więcej informacji, zobacz [Tworzenie rozszerzenia z szablonem elementu edytora](../extensibility/creating-an-extension-with-an-editor-item-template.md).

3. Usuń istniejące pliki klas.

## <a name="implement-an-outlining-tagger"></a>Implementowanie znacznika przedstawiającego
 Regiony nakreślenia są oznaczone rodzajem<xref:Microsoft.VisualStudio.Text.Tagging.OutliningRegionTag>znacznika ( ). Ten tag zapewnia standardowe zachowanie przedstawiające. Zarysowany region można rozwinąć lub zwinąć. Zarysowany region jest oznaczony**+** znakiem Plus ( ), jeśli jest**-** zwinięty lub znakiem Minus ( ), jeśli jest rozwinięty, a rozwinięty region jest wyznaczany przez pionową linię.

 Poniższe kroki pokazują, jak zdefiniować znacznik, który tworzy obszary przedstawiające dla wszystkich regionów rozdzielonych nawiasami (**[**,**]**).

### <a name="to-implement-an-outlining-tagger"></a>Aby zaimplementować znacznik przedstawiający

1. Dodaj plik klasy i `OutliningTagger`nadaj jego nazwę .

2. Zaimportuj następujące obszary nazw.

     [!code-csharp[VSSDKOutlineRegionTest#1](../extensibility/codesnippet/CSharp/walkthrough-outlining_1.cs)]
     [!code-vb[VSSDKOutlineRegionTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_1.vb)]

3. Utwórz klasę `OutliningTagger`o nazwie <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601>i zaimplementuj ją:

     [!code-csharp[VSSDKOutlineRegionTest#2](../extensibility/codesnippet/CSharp/walkthrough-outlining_2.cs)]
     [!code-vb[VSSDKOutlineRegionTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_2.vb)]

4. Dodaj kilka pól, aby śledzić bufor tekstu i migawkę oraz gromadzić zestawy wierszy, które powinny być oznaczane jako regiony konspektowe. Ten kod zawiera listę Region obiektów (do zdefiniowania później), które reprezentują regionów przedstawiających.

     [!code-csharp[VSSDKOutlineRegionTest#3](../extensibility/codesnippet/CSharp/walkthrough-outlining_3.cs)]
     [!code-vb[VSSDKOutlineRegionTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_3.vb)]

5. Dodaj konstruktor tager, który inicjuje pola, analizuje bufor i <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> dodaje program obsługi zdarzeń do zdarzenia.

     [!code-csharp[VSSDKOutlineRegionTest#4](../extensibility/codesnippet/CSharp/walkthrough-outlining_4.cs)]
     [!code-vb[VSSDKOutlineRegionTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_4.vb)]

6. Zaimplementuj <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> metodę, która zawiera wystąpienia tagu. W tym przykładzie przyjęto <xref:Microsoft.VisualStudio.Text.NormalizedSpanCollection> założenie, że zakresy w przeszedł do metody są ciągłe, chociaż nie zawsze może być w przypadku. Ta metoda tworzenie wystąpienia nowego zakresu znaczników dla każdego z regionów przedstawiających.

     [!code-csharp[VSSDKOutlineRegionTest#5](../extensibility/codesnippet/CSharp/walkthrough-outlining_5.cs)]
     [!code-vb[VSSDKOutlineRegionTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_5.vb)]

7. Zadeklaruj `TagsChanged` program obsługi zdarzeń.

     [!code-csharp[VSSDKOutlineRegionTest#6](../extensibility/codesnippet/CSharp/walkthrough-outlining_6.cs)]
     [!code-vb[VSSDKOutlineRegionTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_6.vb)]

8. Dodaj `BufferChanged` program obsługi zdarzeń, <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> który odpowiada na zdarzenia, analizując bufor tekstu.

     [!code-csharp[VSSDKOutlineRegionTest#7](../extensibility/codesnippet/CSharp/walkthrough-outlining_7.cs)]
     [!code-vb[VSSDKOutlineRegionTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_7.vb)]

9. Dodaj metodę, która analizuje bufor. Przykład podany w tym miejscu jest tylko dla ilustracji. Synchronicznie analizuje bufor do zagnieżdżonych regionów przedstawiających.

     [!code-csharp[VSSDKOutlineRegionTest#8](../extensibility/codesnippet/CSharp/walkthrough-outlining_8.cs)]
     [!code-vb[VSSDKOutlineRegionTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_8.vb)]

10. Następująca metoda pomocnika pobiera liczbę całkowitą, która reprezentuje poziom tworzenia ziarskania, tak że 1 jest najbardziej lewicową parą nawiasów klamrowych.

     [!code-csharp[VSSDKOutlineRegionTest#9](../extensibility/codesnippet/CSharp/walkthrough-outlining_9.cs)]
     [!code-vb[VSSDKOutlineRegionTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_9.vb)]

11. Następująca metoda pomocnika tłumaczy Region (zdefiniowane w dalszej części tego artykułu) do SnapshotSpan.

     [!code-csharp[VSSDKOutlineRegionTest#10](../extensibility/codesnippet/CSharp/walkthrough-outlining_10.cs)]
     [!code-vb[VSSDKOutlineRegionTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_10.vb)]

12. Poniższy kod jest tylko do ilustracji. Definiuje partialRegion klasy, która zawiera numer wiersza i przesunięcie początku regionu konspektowego i odwołanie do regionu nadrzędnego (jeśli istnieje). Ten kod umożliwia analizatorowi do konfigurowania zagnieżdżonych regionów tworzenia konfiguracji. Pochodna Klasa Region zawiera odwołanie do numeru wiersza końca regionu obliczynia.

     [!code-csharp[VSSDKOutlineRegionTest#11](../extensibility/codesnippet/CSharp/walkthrough-outlining_11.cs)]
     [!code-vb[VSSDKOutlineRegionTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_11.vb)]

## <a name="implement-a-tagger-provider"></a>Implementowanie dostawcy znaczników
 Wyeksportuj dostawcę znaczników dla tagera. Dostawca znaczników tworzy `OutliningTagger` dla bufora typu zawartości "tekst", albo `OutliningTagger` zwraca, jeśli bufor już go ma.

### <a name="to-implement-a-tagger-provider"></a>Aby zaimplementować dostawcę znacznika

1. Utwórz klasę `OutliningTaggerProvider` o <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider>nazwie, która implementuje program , i wyeksportuj ją za pomocą atrybutów ContentType i TagType.

     [!code-csharp[VSSDKOutlineRegionTest#12](../extensibility/codesnippet/CSharp/walkthrough-outlining_12.cs)]
     [!code-vb[VSSDKOutlineRegionTest#12](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_12.vb)]

2. <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider.CreateTagger%2A> Zaimplementuj `OutliningTagger` metodę, dodając do właściwości buforu.

     [!code-csharp[VSSDKOutlineRegionTest#13](../extensibility/codesnippet/CSharp/walkthrough-outlining_13.cs)]
     [!code-vb[VSSDKOutlineRegionTest#13](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_13.vb)]

## <a name="build-and-test-the-code"></a>Tworzenie i testowanie kodu
 Aby przetestować ten kod, skompiluj rozwiązanie OutlineRegionTest i uruchom go w wystąpieniu eksperymentalnym.

### <a name="to-build-and-test-the-outlineregiontest-solution"></a>Aby skompilować i przetestować rozwiązanie OutlineRegionTest

1. Skompiluj rozwiązanie.

2. Po uruchomieniu tego projektu w debugerze zostanie uruchomione drugie wystąpienie programu Visual Studio.

3. Tworzenie pliku tekstowego. Wpisz tekst zawierający zarówno nawiasy otwierające, jak i nawiasy zamykające.

    ```
    [
       Hello
    ]
    ```

4. Powinien istnieć region tworzenia nakreślenia, który zawiera oba nawiasy. Aby zwinąć obszar konspektu, należy kliknąć znak minus po lewej stronie otwartego nawiasu. Gdy region jest zwinięty, symbol wielokropka (*...*) powinien pojawić się po lewej stronie zwiniętego regionu, a po przesunięciu wskaźnika myszy na wielokropek powinien pojawić się okno podręczne zawierające **tekst.**

## <a name="see-also"></a>Zobacz też
- [Instruktaż: łączenie typu zawartości z rozszerzeniem nazwy pliku](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
