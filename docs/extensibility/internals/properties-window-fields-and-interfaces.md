---
title: Pola i interfejsy okna właściwości | Microsoft Docs
description: Dowiedz się więcej na temat zaznaczenia, które określa, jakie informacje są wyświetlane w okno Właściwości na podstawie okna, które ma fokus w środowisku IDE programu Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Properties window, fields and interfaces
ms.assetid: 0328f0e5-2380-4a7a-a872-b547cb775050
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: eb1f0a0f78b935a3b61596e4dd0b595030640b00
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99970013"
---
# <a name="properties-window-fields-and-interfaces"></a>Pola i interfejsy okna właściwości
Model wyboru służący do określania, jakie informacje są wyświetlane w oknie **Właściwości** , zależy od okna, które ma fokus w środowisku IDE. Każde okno i obiekt w wybranym oknie może mieć obiekt kontekstu zaznaczenia wypychany do globalnego kontekstu wyboru. Środowisko aktualizuje globalny kontekst wyboru przy użyciu wartości z ramki okna, gdy to okno ma fokus. Gdy fokus zmieni się, oznacza to, że kontekst zaznaczenia.

## <a name="tracking-selection-in-the-ide"></a>Śledzenie wyboru w środowisku IDE
 W przypadku ramki okna lub lokacji należącej do IDE jest wywoływana usługa <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection> . Poniższe kroki pokazują, jak zmiana w wyborze, spowodowana przez użytkownika zmiana fokusu na inne otwarte okno lub wybranie innego elementu projektu w **Eksplorator rozwiązań**, jest zaimplementowana w celu zmiany zawartości wyświetlanej w oknie **Właściwości** .

1. Obiekt utworzony przez pakietu VSPackage, który jest zlokalizowany w wybranym oknie wywołuje <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A> do wywołania metody <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection> Invoke <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection> .

2. Kontener wyboru udostępniony przez wybrane okno tworzy własny <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> obiekt. Po zmianie zaznaczenia pakietu VSPackage wywołuje <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> powiadomienia o wszelkich detektorach w środowisku, w tym okna **Właściwości** zmiany. Zapewnia również dostęp do informacji o hierarchii i elementu związanych z nowym wyborem.

3. Wywołanie <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> i przekazanie do niego wybranych elementów hierarchii w `VSHPROPID_BrowseObject` parametrze wypełnia <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> obiekt.

4. Obiekt pochodny [interfejsu IDispatch](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch) jest zwracany dla [__VSHPROPID. VSHPROPID_BrowseObject](<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_BrowseObject>) dla żądanego elementu, a środowisko zawija je do <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> (zobacz poniższy krok). Jeśli wywołanie zakończy się niepowodzeniem, środowisko wykonuje drugie wywołanie `IVsHierarchy::GetProperty` , przekazując do niego kontener wyboru [__VSHPROPID. VSHPROPID_SelContainer](<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_SelContainer>) , że dostarcza element lub elementy hierarchii.

    Projekt pakietu VSPackage nie jest tworzony <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> , ponieważ okno dostarczone przez środowisko pakietu VSPackage, które implementuje go (na przykład **Eksplorator rozwiązań**) konstrukcje <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> w jego imieniu.

5. Środowisko wywołuje metody <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> w celu uzyskania obiektów opartych na `IDispatch` interfejsie do wypełnienia w oknie **Właściwości** .

   Gdy wartość w oknie **Właściwości** zostanie zmieniona, pakietów VSPackage zaimplementować `IVsTrackSelectionEx::OnElementValueChangeEx` i `IVsTrackSelectionEx::OnSelectionChangeEx` Aby zgłosić zmianę wartości elementu. Środowisko następnie wywołuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> lub, <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> Aby zachować informacje wyświetlane w oknie **Właściwości** zsynchronizowane z wartościami właściwości. Aby uzyskać więcej informacji, zobacz [aktualizowanie wartości właściwości w oknie właściwości](#updating-property-values-in-the-properties-window).

   Oprócz wyboru innego elementu projektu w **Eksplorator rozwiązań** , aby wyświetlić właściwości powiązane z tym elementem, można również wybrać inny obiekt z poziomu formularza lub dokumentu przy użyciu listy rozwijanej dostępnej w oknie **Właściwości** . Aby uzyskać więcej informacji, zobacz [Lista obiektów okna właściwości](../../extensibility/internals/properties-window-object-list.md).

   Można zmienić sposób wyświetlania informacji w siatce okna **Właściwości** z alfabetyczne do kategorii i, jeśli jest dostępny, można także otworzyć stronę właściwości dla wybranego obiektu, klikając odpowiednie przyciski w oknie **Właściwości** . Aby uzyskać więcej informacji, zobacz [przyciski okna właściwości](../../extensibility/internals/properties-window-buttons.md) i [strony właściwości](../../extensibility/internals/property-pages.md).

   Wreszcie Dolna część okna **Właściwości** zawiera również opis pola zaznaczonego w siatce okna **Właściwości** . Aby uzyskać więcej informacji, zobacz [pobieranie opisów pól z okna właściwości](#getting-field-descriptions-from-the-properties-window).

## <a name="updating-property-values-in-the-properties-window"></a><a name="updating-property-values-in-the-properties-window"></a> Aktualizowanie wartości właściwości w oknie właściwości
Istnieją dwa sposoby, aby zachować synchronizację okna **Właściwości** ze zmianami wartości właściwości. Pierwszym jest wywołanie <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> interfejsu, który zapewnia dostęp do podstawowych funkcji okna, w tym dostęp do i tworzenie narzędzi i dokumentów systemu Windows udostępnianych w środowisku. Poniższe kroki opisują ten proces synchronizacji.

### <a name="updating-property-values-using-ivsuishell"></a>Aktualizowanie wartości właściwości przy użyciu IVsUIShell

#### <a name="to-update-property-values-using-the-ivsuishell-interface"></a>Aby zaktualizować wartości właściwości przy użyciu interfejsu IVsUIShell

1. Wywoływanie <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> (za poorednictwem <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> usługi) w dowolnym momencie, gdy pakietów VSPackage, projekty lub edytory muszą tworzyć lub wyliczać okna narzędzi lub dokumentów.

2. Zaimplementuj, <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.RefreshPropertyBrowser%2A> Aby zachować synchronizację okna **Właściwości** ze zmianami właściwości dla projektu (lub dowolnym innym wybranym obiektem przeglądanym przez okno **Właściwości** ) bez implementowania <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> i uruchamiania <xref:Microsoft.VisualStudio.OLE.Interop.IPropertyNotifySink.OnChanged%2A> zdarzeń.

3. Wdrażaj <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> metody <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.AdviseHierarchyEvents%2A> i <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.UnadviseHierarchyEvents%2A> ustanawiaj i wyłączaj odpowiednio powiadomienia klienta dotyczące zdarzeń hierarchii bez konieczności implementowania hierarchii <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> .

### <a name="updating-property-values-using-iconnection"></a>Aktualizowanie wartości właściwości przy użyciu IConnection
 Drugi sposób utrzymywania okna **Właściwości** w synchronizacji ze zmianami wartości właściwości ma na celu zaimplementowanie `IConnection` w obiekcie połączonym, aby wskazać istnienie interfejsów wychodzących. Jeśli chcesz zlokalizować nazwę właściwości, Utwórz obiekt z <xref:System.ComponentModel.ICustomTypeDescriptor> . <xref:System.ComponentModel.ICustomTypeDescriptor>Implementacja może zmodyfikować deskryptory właściwości, które zwraca i zmienić nazwę właściwości. Aby zlokalizować opis, Utwórz atrybut pochodzący z <xref:System.ComponentModel.DescriptionAttribute> i Zastąp Właściwość Description.

#### <a name="considerations-in-implementing-the-iconnection-interface"></a>Zagadnienia dotyczące implementacji interfejsu IConnection

1. `IConnection` zapewnia dostęp do podrzędnego obiektu modułu wyliczającego za pomocą <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnectionPoints> interfejsu. Zapewnia również dostęp do wszystkich podobiektów punktu połączenia, z których każdy implementuje <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> interfejs.

2. Każdy obiekt przeglądania jest odpowiedzialny za implementację <xref:Microsoft.VisualStudio.OLE.Interop.IPropertyNotifySink> zdarzenia. Okno **Właściwości** zostanie powiadomione o zdarzeniu ustawionym przez `IConnection` .

3. Punkt połączenia kontroluje liczbę połączeń (co najmniej jeden), które umożliwia w jego implementacji <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.Advise%2A> . Punkt połączenia, który dopuszcza tylko jeden interfejs, może zwracać <xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL> z <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.EnumConnections%2A> metody.

4. Klient może wywołać interfejs, `IConnection` Aby uzyskać dostęp do podrzędnego obiektu modułu wyliczającego z <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnectionPoints> interfejsem. <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnectionPoints>Interfejs można następnie wywołać, aby wyliczyć punkty połączenia dla każdego identyfikatora interfejsu wychodzącego (IID).

5. `IConnection` może być również wywoływana w celu uzyskania dostępu do podobiektów punktu połączenia z <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> interfejsem dla każdego wychodzącego identyfikatora IID. Za pomocą <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> interfejsu klient uruchamia lub kończy pętlę doradczą z obiektem połączonym i synchronizacją klienta. Klient może również wywołać interfejs, <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> Aby uzyskać obiekt modułu wyliczającego z <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnections> interfejsem, aby wyliczyć połączenia, o których wie.

## <a name="getting-field-descriptions-from-the-properties-window"></a><a name="getting-field-descriptions-from-the-properties-window"></a> Pobieranie opisów pól z okna właściwości
W dolnej części okna **Właściwości** obszar opisu zawiera informacje związane z wybranym polem właściwości. Ta funkcja jest domyślnie włączona. Jeśli chcesz ukryć pole Opis, kliknij prawym przyciskiem myszy okno **Właściwości** , a następnie kliknij pozycję **Opis**. Spowoduje to również usunięcie znacznika wyboru obok tytułu **opisu** w oknie menu. Możesz ponownie wyświetlić pole, wykonując te same kroki, aby ponownie włączyć **Opis** .

 Informacje w polu Opis pochodzą z <xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo> . Każda metoda, interfejs, Klasa coclass i tak dalej może mieć atrybut nielokalny `helpstring` w bibliotece typów. Okno **Właściwości** Pobiera ciąg z <xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo.GetDocumentation%2A> .

### <a name="to-specify-localized-help-strings"></a>Aby określić zlokalizowane ciągi pomocy

1. Dodaj `helpstringdll` atrybut do instrukcji Library w bibliotece typów ( `typelib` ).

   > [!NOTE]
   > Ten krok jest opcjonalny, jeśli biblioteka typów znajduje się w pliku biblioteki obiektów (. olb).

2. Określ `helpstringcontext` atrybuty dla ciągów. Można również określić `helpstring` atrybuty.

    Te atrybuty są różne od `helpfile` atrybutów i `helpcontext` , które są zawarte w pliku. chm.

   Aby pobrać informacje o opisach, które mają być wyświetlane dla wyróżnionej nazwy właściwości, okno **Właściwości** wywołuje <xref:System.Runtime.InteropServices.ComTypes.ITypeInfo2.GetDocumentation2%2A> dla wybranej właściwości, określając żądany `lcid` atrybut ciągu danych wyjściowych. Wewnętrznie program <xref:System.Runtime.InteropServices.ComTypes.ITypeInfo2> znajduje plik. dll określony w `helpstringdll` atrybucie i wywołuje plik DLL `DLLGetDocumentation` z określonym kontekstem i `lcid` atrybutem.

   Sygnatura i implementacja programu `DLLGetDocumentation` są:

```cpp
STDAPI DLLGetDocumentation
(
   ITypeLib * /* ptlib */,
   ITypeInfo * /* ptinfo */,
   LCID /* lcid */,
   DWORD dwCtx,
   BSTR * pbstrHelpString
);
```

 `DLLGetDocumentation`Funkcja musi być eksportem zdefiniowanym w pliku. def dla biblioteki DLL.

 Wewnętrznie tworzony jest plik. olb, który jest w rzeczywistości biblioteką DLL. Ta biblioteka DLL zawiera jeden zasób, plik biblioteki typów (. tlb) i jedną funkcję, która została wyeksportowana `DLLGetDocumentation` .

 W przypadku plików. olb `helpstringdll` atrybut jest opcjonalny, ponieważ jest to ten sam plik, który zawiera sam plik. tlb.

 Aby ciągi były wyświetlane w okienku **opisy** , w związku z tym minimalnym wymaganiem jest określenie `helpstring` atrybutu w bibliotece typów. Jeśli chcesz, aby te ciągi były zlokalizowane, musisz określić `helpstringdll` atrybut (opcjonalnie) i `helpstringcontext` atrybut (required) i zaimplementować `DLLGetDocumentation` .

 Nie ma dodatkowych interfejsów, które należy zaimplementować podczas uzyskiwania zlokalizowanych informacji przy użyciu atrybutu IDL `helpstringcontext` i `DLLGetDocumentation` .

 Innym sposobem uzyskania zlokalizowanej nazwy i opisu właściwości jest implementacja <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.GetLocalizedPropertyInfo%2A> . Aby uzyskać więcej informacji dotyczących implementacji tej metody, zobacz [okno właściwości pola i interfejsy](../../extensibility/internals/properties-window-fields-and-interfaces.md).

## <a name="see-also"></a>Zobacz też

- [Rozszerzanie właściwości](../../extensibility/internals/extending-properties.md)
