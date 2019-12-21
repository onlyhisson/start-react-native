# start-react-native

react-native init MyApp

cd MyApp

npm install --save styled-components

npm install --save-dev typescript @types/react @types/react-native @types/styled-components babel-plugin-root-import


***
### tsconfig.json 생성
~~~
{
   "compilerOptions": {
     "allowJs": true,
     "allowSyntheticDefaultImports": true,
     "esModuleInterop": true,
     "isolatedModules": true,
     "jsx": "react",
     "lib": ["es6"],
     "moduleResolution": "node",
     "noEmit": true,
     "strict": true,
     "target": "esnext",
     "baseUrl": "./src",
     "paths": {
       "~/*": ["*"]
     }
   },
   "exclude": [
     "node_modules",
     "babel.config.js",
     "metro.config.js",
     "jest.config.js"
   ]
}
~~~

***
### babel.config.js 파일 수정
~~~
module.exports = {
 presets: ['module:metro-react-native-babel-preset'],
 plugins: [
   [
     'babel-plugin-root-import',
     {
       rootPathPrefix: '~',
       rootPathSuffix: 'src',
     },
   ],
 ],
};
~~~

***
### ./src 폴더 생성
App.js 파일 App.tsx 변경 후 ./src 로 이동

***
### App.tsx 

~~~
import React, { Fragment } from 'react';
import { StatusBar, SafeAreaView } from 'react-native';
 
import {
 Header,
 LearnMoreLinks,
 Colors,
 DebugInstructions,
 ReloadInstructions,
} from 'react-native/Libraries/NewAppScreen';
 
import Styled from 'styled-components/native';
 
const ScrollView = Styled.ScrollView`
 background-color: ${Colors.lighter};
`;
 
const Body = Styled.View`
 background-color: ${Colors.white};
`;
 
const SectionContainer = Styled.View`
 margin-top: 32px;
 padding-horizontal: 24px;
`;
 
const SectionDescription = Styled.Text`
 margin-top: 8px;
 font-size: 18px;
 font-weight: 400;
 color: ${Colors.dark};
`;
 
const HighLight = Styled.Text`
 font-weight: 700;
`;
 
interface Props {}
 
const App = ({  }: Props) => {
 return (
   <Fragment>
     <StatusBar barStyle="dark-content" />
     <SafeAreaView>
       <ScrollView contentInsetAdjustmentBehavior="automatic">
         <Header />
         <Body>
           <SectionContainer>
             <SectionDescription>Step One</SectionDescription>
             <SectionDescription>
               Edit <HighLight>App.js</HighLight> to change this screen and
               then come back to see your edits.
             </SectionDescription>
           </SectionContainer>
           <SectionContainer>
             <SectionDescription>See Your Changes</SectionDescription>
             <SectionDescription>
               <ReloadInstructions />
             </SectionDescription>
           </SectionContainer>
           <SectionContainer>
             <SectionDescription>Debug</SectionDescription>
             <SectionDescription>
               <DebugInstructions />
             </SectionDescription>
           </SectionContainer>
           <SectionContainer>
             <SectionDescription>Learn More</SectionDescription>
             <SectionDescription>
               Read the docs to discover what to do next:
             </SectionDescription>
           </SectionContainer>
           <LearnMoreLinks />
         </Body>
       </ScrollView>
     </SafeAreaView>
   </Fragment>
 );
};
 
export default App;
~~~

***
### index.js 파일 수정 
**import App from ‘./App’;** 를 **import App from ‘~/App’;** 로 변경

***
### 리액트 프로젝트 시작
cd *FULL_PATH*/MyApp && npx react-native run-ios
