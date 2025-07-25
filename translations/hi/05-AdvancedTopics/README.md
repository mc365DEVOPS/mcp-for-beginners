<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "a5c1d9e9856024d23da4a65a847c75ac",
  "translation_date": "2025-07-18T07:13:26+00:00",
  "source_file": "05-AdvancedTopics/README.md",
  "language_code": "hi"
}
-->
# MCP में उन्नत विषय

यह अध्याय Model Context Protocol (MCP) के कार्यान्वयन में कई उन्नत विषयों को कवर करता है, जिनमें मल्टी-मोडल इंटीग्रेशन, स्केलेबिलिटी, सुरक्षा सर्वोत्तम प्रथाएं, और एंटरप्राइज इंटीग्रेशन शामिल हैं। ये विषय मजबूत और प्रोडक्शन-तैयार MCP एप्लिकेशन बनाने के लिए महत्वपूर्ण हैं जो आधुनिक AI सिस्टम की मांगों को पूरा कर सकें।

## अवलोकन

यह पाठ MCP के कार्यान्वयन में उन्नत अवधारणाओं का अन्वेषण करता है, जिसमें मल्टी-मोडल इंटीग्रेशन, स्केलेबिलिटी, सुरक्षा सर्वोत्तम प्रथाएं, और एंटरप्राइज इंटीग्रेशन पर ध्यान केंद्रित किया गया है। ये विषय प्रोडक्शन-ग्रेड MCP एप्लिकेशन बनाने के लिए आवश्यक हैं जो एंटरप्राइज वातावरण में जटिल आवश्यकताओं को संभाल सकें।

## सीखने के उद्देश्य

इस पाठ के अंत तक, आप सक्षम होंगे:

- MCP फ्रेमवर्क के भीतर मल्टी-मोडल क्षमताओं को लागू करना
- उच्च मांग वाले परिदृश्यों के लिए स्केलेबल MCP आर्किटेक्चर डिजाइन करना
- MCP की सुरक्षा सिद्धांतों के अनुरूप सुरक्षा सर्वोत्तम प्रथाओं को लागू करना
- MCP को एंटरप्राइज AI सिस्टम और फ्रेमवर्क के साथ एकीकृत करना
- प्रोडक्शन वातावरण में प्रदर्शन और विश्वसनीयता को अनुकूलित करना

## पाठ और नमूना परियोजनाएं

| लिंक | शीर्षक | विवरण |
|------|-------|-------------|
| [5.1 Integration with Azure](./mcp-integration/README.md) | Azure के साथ इंटीग्रेशन | जानें कि अपने MCP सर्वर को Azure पर कैसे इंटीग्रेट करें |
| [5.2 Multi modal sample](./mcp-multi-modality/README.md) | MCP मल्टी-मोडल नमूने | ऑडियो, इमेज और मल्टी-मोडल प्रतिक्रिया के लिए नमूने |
| [5.3 MCP OAuth2 sample](../../../05-AdvancedTopics/mcp-oauth2-demo) | MCP OAuth2 डेमो | एक न्यूनतम Spring Boot ऐप जो MCP के साथ OAuth2 दिखाता है, दोनों Authorization और Resource Server के रूप में। सुरक्षित टोकन जारी करना, संरक्षित एंडपॉइंट्स, Azure Container Apps पर तैनाती, और API Management इंटीग्रेशन को प्रदर्शित करता है। |
| [5.4 Root Contexts](./mcp-root-contexts/README.md) | रूट कॉन्टेक्स्ट | रूट कॉन्टेक्स्ट के बारे में अधिक जानें और उन्हें कैसे लागू करें |
| [5.5 Routing](./mcp-routing/README.md) | रूटिंग | विभिन्न प्रकार की रूटिंग सीखें |
| [5.6 Sampling](./mcp-sampling/README.md) | सैंपलिंग | सैंपलिंग के साथ काम करना सीखें |
| [5.7 Scaling](./mcp-scaling/README.md) | स्केलिंग | स्केलिंग के बारे में जानें |
| [5.8 Security](./mcp-security/README.md) | सुरक्षा | अपने MCP सर्वर को सुरक्षित करें |
| [5.9 Web Search sample](./web-search-mcp/README.md) | वेब सर्च MCP | Python MCP सर्वर और क्लाइंट जो SerpAPI के साथ रियल-टाइम वेब, न्यूज, प्रोडक्ट सर्च, और Q&A को इंटीग्रेट करता है। मल्टी-टूल ऑर्केस्ट्रेशन, बाहरी API इंटीग्रेशन, और मजबूत त्रुटि प्रबंधन को प्रदर्शित करता है। |
| [5.10 Realtime Streaming](./mcp-realtimestreaming/README.md) | स्ट्रीमिंग | रियल-टाइम डेटा स्ट्रीमिंग आज के डेटा-संचालित विश्व में आवश्यक हो गई है, जहां व्यवसायों और एप्लिकेशन को त्वरित निर्णय लेने के लिए तुरंत जानकारी की आवश्यकता होती है। |
| [5.11 Realtime Web Search](./mcp-realtimesearch/README.md) | वेब सर्च | रियल-टाइम वेब सर्च में MCP कैसे AI मॉडल, सर्च इंजन, और एप्लिकेशन के बीच कॉन्टेक्स्ट प्रबंधन के लिए एक मानकीकृत दृष्टिकोण प्रदान करता है। |
| [5.12  Entra ID Authentication for Model Context Protocol Servers](./mcp-security-entra/README.md) | Entra ID प्रमाणीकरण | Microsoft Entra ID एक मजबूत क्लाउड-आधारित पहचान और एक्सेस प्रबंधन समाधान प्रदान करता है, जो सुनिश्चित करता है कि केवल अधिकृत उपयोगकर्ता और एप्लिकेशन ही आपके MCP सर्वर के साथ इंटरैक्ट कर सकें। |
| [5.13 Azure AI Foundry Agent Integration](./mcp-foundry-agent-integration/README.md) | Azure AI Foundry इंटीग्रेशन | जानें कि Model Context Protocol सर्वरों को Azure AI Foundry एजेंट्स के साथ कैसे इंटीग्रेट करें, जिससे शक्तिशाली टूल ऑर्केस्ट्रेशन और एंटरप्राइज AI क्षमताएं मानकीकृत बाहरी डेटा स्रोत कनेक्शनों के साथ सक्षम होती हैं। |
| [5.14 Context Engineering](./mcp-contextengineering/README.md) | कॉन्टेक्स्ट इंजीनियरिंग | MCP सर्वरों के लिए कॉन्टेक्स्ट इंजीनियरिंग तकनीकों का भविष्य, जिसमें कॉन्टेक्स्ट अनुकूलन, डायनेमिक कॉन्टेक्स्ट प्रबंधन, और MCP फ्रेमवर्क के भीतर प्रभावी प्रॉम्प्ट इंजीनियरिंग के लिए रणनीतियां शामिल हैं। |

## अतिरिक्त संदर्भ

उन्नत MCP विषयों पर सबसे अद्यतित जानकारी के लिए देखें:
- [MCP Documentation](https://modelcontextprotocol.io/)
- [MCP Specification](https://spec.modelcontextprotocol.io/)
- [GitHub Repository](https://github.com/modelcontextprotocol)

## मुख्य निष्कर्ष

- मल्टी-मोडल MCP कार्यान्वयन AI क्षमताओं को केवल टेक्स्ट प्रोसेसिंग से आगे बढ़ाते हैं
- स्केलेबिलिटी एंटरप्राइज तैनाती के लिए आवश्यक है और इसे हॉरिजॉन्टल और वर्टिकल स्केलिंग के माध्यम से संबोधित किया जा सकता है
- व्यापक सुरक्षा उपाय डेटा की सुरक्षा करते हैं और उचित एक्सेस नियंत्रण सुनिश्चित करते हैं
- Azure OpenAI और Microsoft AI Foundry जैसे प्लेटफॉर्म के साथ एंटरप्राइज इंटीग्रेशन MCP क्षमताओं को बढ़ाता है
- उन्नत MCP कार्यान्वयन अनुकूलित आर्किटेक्चर और सावधानीपूर्वक संसाधन प्रबंधन से लाभान्वित होते हैं

## अभ्यास

किसी विशिष्ट उपयोग मामले के लिए एंटरप्राइज-ग्रेड MCP कार्यान्वयन डिजाइन करें:

1. अपने उपयोग मामले के लिए मल्टी-मोडल आवश्यकताओं की पहचान करें
2. संवेदनशील डेटा की सुरक्षा के लिए आवश्यक सुरक्षा नियंत्रणों का रूपरेखा तैयार करें
3. एक स्केलेबल आर्किटेक्चर डिजाइन करें जो विभिन्न लोड को संभाल सके
4. एंटरप्राइज AI सिस्टम के साथ इंटीग्रेशन पॉइंट्स की योजना बनाएं
5. संभावित प्रदर्शन बाधाओं और उनके निवारण रणनीतियों का दस्तावेजीकरण करें

## अतिरिक्त संसाधन

- [Azure OpenAI Documentation](https://learn.microsoft.com/en-us/azure/ai-services/openai/)
- [Microsoft AI Foundry Documentation](https://learn.microsoft.com/en-us/ai-services/)

---

## आगे क्या है

- [5.1 MCP Integration](./mcp-integration/README.md)

**अस्वीकरण**:  
यह दस्तावेज़ AI अनुवाद सेवा [Co-op Translator](https://github.com/Azure/co-op-translator) का उपयोग करके अनुवादित किया गया है। जबकि हम सटीकता के लिए प्रयासरत हैं, कृपया ध्यान दें कि स्वचालित अनुवादों में त्रुटियाँ या अशुद्धियाँ हो सकती हैं। मूल दस्तावेज़ अपनी मूल भाषा में ही अधिकारिक स्रोत माना जाना चाहिए। महत्वपूर्ण जानकारी के लिए, पेशेवर मानव अनुवाद की सलाह दी जाती है। इस अनुवाद के उपयोग से उत्पन्न किसी भी गलतफहमी या गलत व्याख्या के लिए हम जिम्मेदार नहीं हैं।