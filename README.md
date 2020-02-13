# Softwareproject1
 Group project 

#include "dotdatabase.hpp"
#include <tinyxml2.cpp>
#include <tinyxml2.h>
#include <string>
#include <vector>

//hold values
struct Document
{
    std::string title;
    std::string body;
    std::vector<std::string> places;
    std::vector<std::string> topics;
};

//parses the XML file that parses the XML-formatted file
static std::string getElementText(tinyxml2::XMLElement *_element);
static std::vector<std::string> getTextList(tinyxml2::XMLElement *_element);
static void printDoc(Document* doc);

int main(int argc, const char * argv[])
{
    tinyml2::XMLDocument doc;
    doc.LoadFile("/Users/cortneybramlett/Downloads/NAD_r3_revised_ASCII");
     
    //to check that the file loaded
    if(doc.ErrorID() == 0) {
        tinyxml2::XMLElement *pRoot;
        
        //to set the first element in the file
        pRoot = doc.FirstChildElement("STATES");
                
        //While this node points to a parent node called "STATES"
        while(pRoot) {
            Document * thisDoc = new Document ();
                  
            //Getting the title in <state><text><title...</title></text></states>
            thisDoc->title = getElementText(pRoot->FirstChildElement("TEXT")->FirstChildElement("TITLE"));
            thisDoc->body = getElementText (pRoot->FirstChildElement("TEXT")->FirstChildElement("BODY"));
             
            //calling the function to get the list of places and topics
            thisDoc->places = getTextList(pRoot->FirstChildElement("PLACES"));
            thisDoc->topics = getTextList(pRoot->FirstChildElement("TOPICS"));
                                                                               
            printDoc(thisDoc);
                                                                               
            pRoot = pRoot->NextSiblingElement("STATES");
        }
    }
    return 0;
    
    //gets a value so long as the node is not null
    static std::string getElementText(tinyxml2::XMLElement *_element)
    {
        std::string value;
        if(_element !=NULL)
        {
            value = _element->GetText();
        }
        return value;
    }
    
    //gets a list of elements within "D" tags in an element, then puts them in a vector
    static std::vector<std::string> getTextList(tinysml2::XMLElement *element)
    {
        tinyxml2::XMLElement *pRoot;
        std::vector<std::string> strings;
        if(_element !=NULL)
        {
            pRoot = _element->FirstChildElement("D");
            while(pRoot)
            {
                strings.push_back(pRoot->GetText());
                pRoot = pRoot->NextSiblingElement("D");
            
            }
        }
        return strings;
        
        }
    
    //print out what was parsed
    static void printDoc(Document* _doc)
    {
        std::cout << "Title: " << _doc->title << std::endl;
        std::cout << "Places: " << std::endl;
        for(auto & place : _doc->places)
        {
            std::cout << "\t" << place << std::endl;
            
        }
        std::cout << "Topics:" << std::endl;
        for(auto & topic : _doc->topics)
        {
            std::cout << "\t" << topic << std::endl;
        }
        std::cout << "Body:" << std::endl;
        std::cout << _doc->body << std::endl;
    }
    </std::string></std::string></std::string></std::string></std::string></vector></string></iostream>
    
 

