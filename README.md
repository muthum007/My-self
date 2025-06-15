import { resumeData } from './data';

// SVG Icons for contact details
const PhoneIcon = () => (
  <svg xmlns="http://www.w3.org/2000/svg" className="h-4 w-4 mr-2 inline-block" fill="none" viewBox="0 0 24 24" stroke="currentColor" strokeWidth={2}>
    <path strokeLinecap="round" strokeLinejoin="round" d="M3 5a2 2 0 012-2h3.28a1 1 0 01.948.684l1.498 4.493a1 1 0 01-.502 1.21l-2.257 1.13a11.042 11.042 0 005.516 5.516l1.13-2.257a1 1 0 011.21-.502l4.493 1.498a1 1 0 01.684.949V19a2 2 0 01-2 2h-1C9.716 21 3 14.284 3 6V5z" />
  </svg>
);

const EmailIcon = () => (
  <svg xmlns="http://www.w3.org/2000/svg" className="h-4 w-4 mr-2 inline-block" fill="none" viewBox="0 0 24 24" stroke="currentColor" strokeWidth={2}>
    <path strokeLinecap="round" strokeLinejoin="round" d="M3 8l7.89 5.26a2 2 0 002.22 0L21 8M5 19h14a2 2 0 002-2V7a2 2 0 00-2-2H5a2 2 0 00-2 2v10a2 2 0 002 2z" />
  </svg>
);

// Section component for consistent styling
const Section: React.FC<{ title: string; children: React.ReactNode }> = ({ title, children }) => (
  <section className="mb-8">
    <h2 className="text-2xl font-bold text-gray-800 border-b-2 border-gray-300 pb-2 mb-4">
      {title}
    </h2>
    {children}
  </section>
);

// Main Page Component
export default function PortfolioPage() {
  const { name, phone, email, experience, education, skills } = resumeData;

  return (
    <div className="bg-gray-50 min-h-screen font-sans">
      <main className="container mx-auto max-w-4xl p-4 sm:p-8">
        <div className="bg-white shadow-xl rounded-lg p-6 sm:p-10">
          {/* Header */}
          <header className="text-center mb-10">
            <h1 className="text-4xl sm:text-5xl font-extrabold text-gray-900 tracking-tight">
              {name}
            </h1>
            <div className="flex justify-center items-center flex-wrap gap-x-6 gap-y-2 mt-4 text-gray-600">
              <a href={`tel:${phone}`} className="hover:text-blue-600 transition-colors duration-300 flex items-center">
                <PhoneIcon />
                {phone}
              </a>
              <a href={`mailto:${email}`} className="hover:text-blue-600 transition-colors duration-300 flex items-center">
                <EmailIcon />
                {email}
              </a>
            </div>
          </header>

          {/* Professional Experience */}
          <Section title="Professional Experience">
            <div className="space-y-8">
              {experience.map((job, index) => (
                <div key={index}>
                  <div className="flex justify-between items-baseline flex-wrap">
                    <h3 className="text-xl font-semibold text-gray-900">{job.role}</h3>
                    <p className="text-sm text-gray-500">{job.period}</p>
                  </div>
                  <p className="text-md text-gray-700 font-medium">{job.company}</p>
                  <p className="text-sm text-gray-500 mb-3">{job.location}</p>
                  <ul className="list-disc list-inside space-y-2 text-gray-700">
                    {job.description.map((desc, i) => (
                      <li key={i}>{desc}</li>
                    ))}
                  </ul>
                </div>
              ))}
            </div>
          </Section>

          {/* Education */}
          <Section title="Education">
            <div className="space-y-4">
              {education.map((edu, index) => (
                <div key={index}>
                  <div className="flex justify-between items-baseline flex-wrap">
                    <h3 className="text-lg font-semibold text-gray-900">{edu.degree}</h3>
                    <p className="text-sm text-gray-500">{edu.period}</p>
                  </div>
                  <p className="text-md text-gray-700">{edu.institution}</p>
                  <p className="text-sm text-gray-600">{edu.grade}</p>
                </div>
              ))}
            </div>
          </Section>

          {/* Skills */}
          <Section title="Technical Skills">
            <div className="space-y-4">
              <div>
                <h3 className="text-lg font-semibold text-gray-800 mb-2">Languages & Scripting</h3>
                <div className="flex flex-wrap gap-2">
                  {skills.languages.map((skill, index) => (
                    <span key={index} className="bg-blue-100 text-blue-800 text-sm font-medium px-3 py-1 rounded-full">
                      {skill}
                    </span>
                  ))}
                </div>
              </div>
              <div>
                <h3 className="text-lg font-semibold text-gray-800 mb-2">Cloud & Big Data Platforms</h3>
                 <div className="flex flex-wrap gap-2">
                  {skills.cloudPlatforms.map((skill, index) => (
                    <span key={index} className="bg-green-100 text-green-800 text-sm font-medium px-3 py-1 rounded-full">
                      {skill}
                    </span>
                  ))}
                </div>
              </div>
            </div>
          </Section>
        </div>
      </main>
    </div>
  );
}
