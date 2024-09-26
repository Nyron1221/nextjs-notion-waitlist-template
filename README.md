import React, { useState } from 'react';
import { Alert, AlertDescription, AlertTitle } from '@/components/ui/alert';
import { Button } from '@/components/ui/button';
import { Input } from '@/components/ui/input';

const WaitlistForm = () => {
  const [email, setEmail] = useState('');
  const [submitted, setSubmitted] = useState(false);

  const handleSubmit = (e) => {
    e.preventDefault();
    // Here you would typically send the email to your backend
    console.log('Email submitted:', email);
    setSubmitted(true);
    setEmail('');
  };

  return (
    <div className="max-w-md mx-auto mt-10 p-6 bg-white rounded-lg shadow-md">
      <h2 className="text-2xl font-bold mb-4 text-center">Join Our Waitlist</h2>
      <p className="mb-4 text-center">Be the first to know when Tyler's Home Good Store launches!</p>
      
      {!submitted ? (
        <form onSubmit={handleSubmit} className="space-y-4">
          <Input
            type="email"
            placeholder="Enter your email"
            value={email}
            onChange={(e) => setEmail(e.target.value)}
            required
            className="w-full"
          />
          <Button type="submit" className="w-full">
            Join Waitlist
          </Button>
        </form>
      ) : (
        <Alert>
          <AlertTitle>Success!</AlertTitle>
          <AlertDescription>
            You've been added to our waitlist. We'll notify you when we launch!
          </AlertDescription>
        </Alert>
      )}
    </div>
  );
};

export default WaitlistForm;
