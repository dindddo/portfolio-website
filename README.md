// app/layout.tsx
import type { Metadata } from "next";
import { Inter } from "next/font/google";
import "./globals.css";

const inter = Inter({ subsets: ["latin"] });

export const metadata: Metadata = {
  title: "PM Portfolio",
  description: "Product Manager Portfolio Website",
};

export default function RootLayout({
  children,
}: {
  children: React.ReactNode;
}) {
  return (
    <html lang="ko">
      <body className={inter.className}>{children}</body>
    </html>
  );
}

// app/page.tsx
import HeroSection from "@/components/HeroSection";
import ExperienceSection from "@/components/ExperienceSection";
import ProfileSection from "@/components/ProfileSection";
import ProjectSection from "@/components/ProjectSection";

export default function Home() {
  // 페이지의 메인 컴포넌트로, 각 섹션을 순차적으로 배치합니다
  return (
    <main className="min-h-screen">
      <HeroSection />
      <ExperienceSection />
      <ProfileSection />
      <ProjectSection />
    </main>
  );
}

// components/HeroSection.tsx
export default function HeroSection() {
  return (
    <section className="py-20 bg-gradient-to-r from-blue-50 via-indigo-50 to-purple-50">
      <div className="container mx-auto px-4 text-center">
        <h1 className="text-4xl md:text-5xl font-bold mb-6 text-gray-900">
          데이터 기반으로 사용자 중심 서비스를 설계하는 Product Manager입니다.
        </h1>
        <p className="text-xl md:text-2xl text-gray-700">
          서비스 전환율 30% 개선, 고객 만족도 20% 향상
        </p>
      </div>
    </section>
  );
}

// components/ExperienceSection.tsx
import { Card, CardContent, CardHeader, CardTitle } from "@/components/ui/card";
import { Button } from "@/components/ui/button";

const experiences = [
  {
    company: "회사 A",
    role: "Product Manager",
    achievement: "월 사용자 50% 증가, 결제 성공률 20% 개선",
  },
  {
    company: "회사 B",
    role: "플랫폼 기획자",
    achievement: "프로세스 자동화로 운영 비용 30% 절감",
  },
  {
    company: "프리랜스 프로젝트",
    role: "Product Manager",
    achievement: "사용자 피드백 기반 기능 개선으로 만족도 15% 증가",
  },
];

export default function ExperienceSection() {
  return (
    <section className="py-16 bg-white">
      <div className="container mx-auto px-4">
        <h2 className="text-3xl font-bold mb-12 text-center">주요 경력</h2>
        <div className="grid grid-cols-1 md:grid-cols-3 gap-8">
          {experiences.map((exp, index) => (
            <Card key={index} className="shadow-lg hover:shadow-xl transition-shadow duration-300">
              <CardHeader>
                <CardTitle>{exp.company}</CardTitle>
                <p className="text-gray-600">{exp.role}</p>
              </CardHeader>
              <CardContent>
                <p className="text-gray-700 mb-6">{exp.achievement}</p>
                <Button className="w-full">자세히 보기</Button>
              </CardContent>
            </Card>
          ))}
        </div>
      </div>
    </section>
  );
}

// components/ProfileSection.tsx
import Image from "next/image";
import { Card, CardContent } from "@/components/ui/card";

export default function ProfileSection() {
  return (
    <section className="py-16 bg-gray-50">
      <div className="container mx-auto px-4">
        <Card className="p-8">
          <div className="grid grid-cols-1 md:grid-cols-2 gap-12 items-center">
            <div className="relative aspect-square w-full max-w-md mx-auto">
              <Image
                src="/api/placeholder/400/400"
                alt="Profile"
                layout="fill"
                objectFit="cover"
                className="rounded-lg"
              />
            </div>
            <div>
              <h2 className="text-3xl font-bold mb-6">About Me</h2>
              <p className="text-gray-700 mb-8">
                7년간 플랫폼 기획 및 데이터 기반 문제 해결에 주력하며 고객 중심 서비스를 설계했습니다.
              </p>
              <div className="mb-6">
                <h3 className="text-xl font-semibold mb-3">주요 도구</h3>
                <p className="text-gray-600">Jira, Confluence, Redash, SQL 등</p>
              </div>
              <div>
                <h3 className="text-xl font-semibold mb-3">직무 철학</h3>
                <p className="text-gray-600">
                  데이터와 사용자 경험을 결합해 문제를 해결하고, 효율적이고 확장 가능한 플랫폼 구축에 중점을 둡니다.
                </p>
              </div>
            </div>
          </div>
        </Card>
      </div>
    </section>
  );
}

// components/ProjectSection.tsx
import { Card, CardContent, CardHeader, CardTitle } from "@/components/ui/card";
import { LineChart, Line, XAxis, YAxis, CartesianGrid, Tooltip, ResponsiveContainer } from 'recharts';

const data = [
  { name: '1월', accuracy: 75 },
  { name: '2월', accuracy: 82 },
  { name: '3월', accuracy: 88 },
  { name: '4월', accuracy: 95 },
];

export default function ProjectSection() {
  return (
    <section className="py-16 bg-white">
      <div className="container mx-auto px-4">
        <Card className="p-8">
          <CardHeader>
            <CardTitle className="text-3xl mb-6">배달 플랫폼 개선 프로젝트</CardTitle>
          </CardHeader>
          <CardContent>
            <div className="grid grid-cols-1 md:grid-cols-2 gap-12">
              <div>
                <div className="mb-8">
                  <h3 className="text-xl font-semibold mb-3">문제 정의</h3>
                  <p className="text-gray-700">
                    배달 ETA의 정확도가 낮아 사용자 불만 증가.
                  </p>
                </div>
                <div className="mb-8">
                  <h3 className="text-xl font-semibold mb-3">해결 방법</h3>
                  <p className="text-gray-700">
                    라이더 배정 알고리즘 최적화 및 데이터 분석 도입.
                  </p>
                </div>
                <div className="mb-8">
                  <h3 className="text-xl font-semibold mb-3">성과</h3>
                  <p className="text-gray-700">
                    ETA 정확도 25% 향상, NPS 15% 증가.
                  </p>
                </div>
                <div>
                  <h3 className="text-xl font-semibold mb-3">사용 도구</h3>
                  <p className="text-gray-700">Jira, Zeppelin, SQL</p>
                </div>
              </div>
              <div className="h-80">
                <ResponsiveContainer width="100%" height="100%">
                  <LineChart data={data}>
                    <CartesianGrid strokeDasharray="3 3" />
                    <XAxis dataKey="name" />
                    <YAxis />
                    <Tooltip />
                    <Line type="monotone" dataKey="accuracy" stroke="#8884d8" />
                  </LineChart>
                </ResponsiveContainer>
              </div>
            </div>
          </CardContent>
        </Card>
      </div>
    </section>
  );
}
